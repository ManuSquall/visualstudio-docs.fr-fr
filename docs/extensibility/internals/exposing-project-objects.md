---
title: Exposer les objets du projet (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708469"
---
# <a name="expose-project-objects"></a>Exposer les objets du projet

Les types de projets personnalisés peuvent fournir des objets d’automatisation afin de permettre l’accès au projet à l’aide d’interfaces d’automatisation. Chaque type de projet est <xref:EnvDTE.Project> censé fournir l’objet d’automatisation standard qui est accessible à partir de <xref:EnvDTE.Solution>, qui contient une collection de tous les projets qui sont ouverts dans l’IDE. Chaque élément du projet devrait être <xref:EnvDTE.ProjectItem> exposé par `Project.ProjectItems`un objet accessible avec . En plus de ces objets d’automatisation standard, les projets peuvent choisir d’offrir des objets d’automatisation spécifiques au projet.

Vous pouvez créer des objets d’automatisation personnalisés au niveau des `DTE.<customObjectName>` racines `DTE.GetObject("<customObjectName>")`que vous pouvez accéder en retard à partir de l’objet DTE racine à l’aide ou . Par exemple, Visual CMMD crée une collection de projets spécifique au projet CMD `DTE.GetObject("VCProjects")`appelée *VCProjects* que vous pouvez accéder à l’utilisation `DTE.VCProjects` ou . Vous pouvez également `Project.Object`créer un , qui est `Project.CodeModel`unique pour le type de projet, un `ProjectItem`, qui `ProjectItem.Object` peut `ProjectItem.FileCodeModel`être interrogé pour son objet le plus dérivé, et un , qui expose et a .

Il s’agit d’une convention commune pour les projets d’exposer une collection de projets personnalisées et spécifiques à un projet. Par exemple, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crée une collection de projet spécifique `DTE.VCProjects` À `DTE.GetObject("VCProjects")`CMD que vous pouvez ensuite accéder à l’utilisation ou . Vous pouvez également `Project.Object`créer un , qui est `Project.CodeModel`unique pour le type de projet, un `ProjectItem`, qui `ProjectItem.Object`peut `ProjectItem.FileCodeModel`être interrogé pour son objet le plus dérivé, un , qui expose , et a .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Contribuer à un objet spécifique à VSPackage pour un projet

1. Ajoutez les clés appropriées au fichier *.pkgdef* de votre VSPackage.

     Voici, par exemple, les paramètres *.pkgdef* du projet linguistique CMD :

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> le code dans la méthode, comme dans l’exemple suivant.

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

     Dans le `g_wszAutomationProjects` code, est le nom de votre collection de projet. La `GetAutomationProjects` méthode crée un objet `Projects` qui implémente l’interface et renvoie un `IDispatch` pointeur à l’objet d’appel, comme indiqué dans l’exemple de code suivant.

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

     Choisissez un nom unique pour votre objet d’automatisation. Les conflits de noms sont imprévisibles, et les collisions font jeter arbitrairement un nom d’objet contradictoire si plusieurs types de projets utilisent le même nom. Vous devez inclure votre nom d’entreprise ou un aspect unique de son nom de produit au nom de l’objet d’automatisation.

     L’objet de collecte personnalisé `Projects` est un point d’entrée pratique pour la partie restante de votre modèle d’automatisation de projet. Votre objet de projet <xref:EnvDTE.Solution> est également accessible à partir de la collection du projet. Une fois que vous avez créé les `Projects` entrées de code et de registre appropriées qui fournissent aux consommateurs des objets de collecte, votre implémentation doit fournir les objets standard restants pour le modèle de projet. Pour plus d’informations, voir [modélisation du projet](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
