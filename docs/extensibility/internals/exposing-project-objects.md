---
title: Exposer des objets du projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f29ca84669f563da5733c8c07b219d498ccf6ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-project-objects"></a>Exposer des objets du projet
Les types de projet personnalisés peuvent fournir des objets automation afin d’autoriser l’accès au projet à l’aide des interfaces automation. Chaque type de projet est censé fournir la norme <xref:EnvDTE.Project> accessible à partir de l’objet automation <xref:EnvDTE.Solution>, qui contient une collection de tous les projets ouverts dans l’IDE. Chaque élément dans le projet est censé être exposé par un <xref:EnvDTE.ProjectItem> objet accédé avec `Project.ProjectItems`. En plus de ces objets automation standard, projets peuvent choisir d’offrir des objets spécifiques au projet automation.  
  
 Vous pouvez créer personnalisées au niveau racine objets automation auquel vous pouvez accéder à liaison tardive à partir de l’objet DTE racine à l’aide `DTE.<customeObjectName>` ou `DTE.GetObject("<customObjectName>")`. Par exemple, Visual C++ crée la collection de projet spécifique à un projet C++ appelée « VCProjects », vous pouvez accéder à l’aide de DTE. VCProjects ou DTE. Par exemple, DTE. Vous pouvez également créer un Project.Object, qui est unique pour le type de projet, Project.CodeModel, ce qui peut être interrogé pour son objet ProjectItem, laquelle expose ProjectItem.Object et un ProjectItem.FileCodeModel plus dérivé.  
  
 Il s’agit d’une convention commune pour les projets exposer une collection de projets personnalisés, spécifique au projet. Par exemple, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crée une collection de projets spécifiques de C++ que vous pouvez ensuite accéder à l’aide de `DTE.VCProjects` ou `DTE.GetObject("VCProjects")`. Vous pouvez également créer un `Project.Object`, qui est unique pour le type de projet, un `Project.CodeModel`, qui peuvent être interrogé pour son objet le plus dérivé, un `ProjectItem`, qui expose `ProjectItem.Object`et un `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Contribuer d’un objet de VSPackage spécifique pour un projet  
  
1.  Ajoutez les clés appropriées dans le fichier .pkgdef de votre VSPackage.  
  
     Par exemple, voici les paramètres .pkgdef pour le projet de langage C++ :  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implémenter le code dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode, comme dans l’exemple suivant.  
  
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
  
     Dans le code, `g_wszAutomationProjects` est le nom de votre collection de projets. Le `GetAutomationProjects` méthode crée un objet qui implémente le `Projects` interface et retourne un `IDispatch` pointeur vers l’objet appelant, comme illustré dans l’exemple de code suivant.  
  
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
  
     Vous devez choisir un nom unique pour votre objet automation. Conflits de noms sont imprévisibles et provoquent des collisions un nom d’objet en conflit être arbitrairement exclues si plusieurs types de projets utilisent le même nom. Vous devez inclure le nom de votre société ou un aspect unique de son nom de produit dans le nom de l’objet automation.  
  
     Personnalisé `Projects` objet de collection est un point d’entrée de commodité pour la partie restante de votre modèle automation de projet. Objet de votre projet est également accessible à partir de la <xref:EnvDTE.Solution> collection de projets. Après avoir créé les entrées appropriées de code et de Registre qui fournissent aux consommateurs avec `Projects` objets de collection, votre implémentation doit fournir restant objets standard pour le modèle de projet. Pour plus d’informations, consultez [projet de modélisation](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>