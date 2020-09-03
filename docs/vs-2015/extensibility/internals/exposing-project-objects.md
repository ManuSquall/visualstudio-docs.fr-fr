---
title: Exposition d’objets Project | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196641"
---
# <a name="exposing-project-objects"></a>Exposition des objets de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les types de projets personnalisés peuvent fournir des objets Automation afin d’autoriser l’accès au projet à l’aide d’interfaces d’automatisation. Chaque type de projet doit fournir l' <xref:EnvDTE.Project> objet Automation Standard accessible à partir de <xref:EnvDTE.Solution> , qui contient une collection de tous les projets ouverts dans l’IDE. Chaque élément du projet est supposé être exposé par un <xref:EnvDTE.ProjectItem> objet accessible avec <xref:EnvDTE.Project.ProjectItems> . En plus de ces objets Automation Standard, les projets peuvent choisir d’offrir des objets Automation spécifiques au projet.  
  
 Vous pouvez créer des objets Automation de niveau racine personnalisés auxquels vous pouvez accéder à liaison tardive à partir de l’objet DTE racine à l’aide de `DTE.<customeObjectName>` ou de `DTE.GetObject(“<customObjectName>”)` . Par exemple, Visual C++ crée une collection de projets C++ spécifique à un projet appelée « VCProjects » à laquelle vous pouvez accéder à l’aide de DTE. VCProjects ou DTE. GetObject ("VCProjects"). Vous pouvez également créer un projet. Object, qui est unique pour le type de projet, un projet. CodeModel, qui peut être interrogé pour son objet le plus dérivé, ProjectItem, qui expose ProjectItem. Object et un ProjectItem. FileCodeModel.  
  
 Il s’agit d’une convention courante pour les projets qui exposent une collection de projets personnalisée spécifique au projet. Par exemple, [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] crée une collection de projets spécifique à C++ que vous pouvez ensuite accéder à l’aide `DTE.VCProjects` de ou de `DTE.GetObject("VCProjects")` . Vous pouvez également créer un `Project.Object` , qui est unique pour le type de projet, un `Project.CodeModel` , qui peut être interrogé pour son objet le plus dérivé, un `ProjectItem` , qui expose `ProjectItem.Object` et un `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Pour fournir un objet spécifique au VSPackage pour un projet  
  
1. Ajoutez les clés appropriées au fichier. pkgdef de votre VSPackage.  
  
     Par exemple, Voici les paramètres. pkgdef pour le projet de langage C++ :  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Implémentez le code dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode, comme dans l’exemple suivant.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     Dans le code, `g_wszAutomationProjects` est le nom de votre collection de projets. La `GetAutomationProjects` méthode crée un objet qui implémente l' `Projects` interface et retourne un `IDispatch` pointeur vers l’objet appelant, comme indiqué dans l’exemple de code suivant.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Vous devez choisir un nom unique pour votre objet Automation. Les conflits de noms sont imprévisibles, et les collisions entraînent la levée arbitraire d’un nom d’objet conflictuel si plusieurs types de projets utilisent le même nom. Vous devez inclure le nom de votre entreprise ou un aspect unique de son nom de produit dans le nom de l’objet Automation.  
  
     L' `Projects` objet de collection personnalisé est un point d’entrée pratique pour la partie restante de votre modèle Automation de projet. Votre objet de projet est également accessible à partir de la <xref:EnvDTE.Solution> collection de projets. Une fois que vous avez créé le code et les entrées de registre appropriés qui fournissent aux consommateurs des `Projects` objets de collection, votre implémentation doit fournir les autres objets standard pour le modèle de projet. Pour plus d’informations, consultez [modélisation de projet](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
