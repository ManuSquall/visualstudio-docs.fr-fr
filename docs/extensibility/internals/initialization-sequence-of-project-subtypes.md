---
title: Séquence d’initialisation des sous-types de projet | Microsoft Docs
description: En savoir plus sur la séquence d’initialisation dans l’environnement Visual Studio pour un système de projet agrégé par plusieurs sous-types de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86173253c947be5de8600e15b68a6f08504803a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839844"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Séquence d’initialisation des sous-types de projets
L’environnement construit un projet en appelant l’implémentation de la fabrique de projet de base de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . La construction d’un sous-type de projet démarre lorsque l’environnement détermine que la liste de GUID de type de projet pour l’extension d’un fichier projet n’est pas vide. L’extension de fichier projet et le GUID du projet spécifient si le projet est un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] type de projet ou. Par exemple, l’extension. vbproj et {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifient un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisation de l’environnement des sous-types de projet
 La procédure suivante détaille la séquence d’initialisation pour un système de projet agrégé par plusieurs sous-types de projet.

1. L’environnement appelle le du projet de base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> et, tandis que le projet analyse son fichier projet, il découvre que la liste des GUID de type de projet d’agrégation n’est pas `null` . Le projet interrompt la création directe de son projet.

2. Le projet appelle `QueryService` sur le <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> service pour créer un sous-type de projet à l’aide de l’implémentation de l’environnement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> méthode. Dans cette méthode, l’environnement effectue des appels de fonctions récursives à vos implémentations de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> et des <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> méthodes pendant qu’il parcourt la liste des GUID de type de projet, en commençant par le sous-type de projet le plus à l’extérieur.

     Les étapes d’initialisation sont détaillées ci-dessous.

    1. L’implémentation de l’environnement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> méthode appelle la `HrCreateInnerProj` méthode avec la déclaration de fonction suivante :

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Lorsque cette fonction est appelée pour la première fois, autrement dit, pour le sous-type de projet le plus à l’extérieur, les paramètres `pOuter` et `pOwner` sont passés en tant que `null` et la fonction définit le sous-type de projet le plus à l’extérieur `IUnknown` sur `pOuter` .

    2. Ensuite, l’environnement appelle la `HrCreateInnerProj` fonction avec le deuxième GUID du type de projet dans la liste. Ce GUID correspond au deuxième sous-type de projet interne pas à pas détaillé dans le projet de base dans la séquence d’agrégation.

    3. Le `pOuter` se pointe maintenant sur le `IUnknown` du sous-type de projet le plus à l’extérieur et `HrCreateInnerProj` appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> suivie d’un appel à votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> la méthode, vous transmettez le contrôle du sous- `IUnknown` type de projet le plus à l’extérieur, `pOuter` . Le projet détenu (sous-type de projet interne) doit créer son objet de projet d’agrégation ici. Dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implémentation de méthode, vous transmettez un pointeur vers le `IUnknown` du projet interne qui est agrégé. Ces deux méthodes créent l’objet d’agrégation, et vos implémentations doivent suivre les règles d’agrégation COM pour s’assurer qu’un sous-type de projet ne finit pas de contenir un décompte de références à lui-même.

    4. `HrCreateInnerProj` appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . Dans cette méthode, le sous-type de projet effectue son travail d’initialisation. Vous pouvez, par exemple, inscrire des événements de solution dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` est appelé de manière récursive jusqu’à ce que le dernier GUID (le projet de base) dans la liste soit atteint. Pour chacun de ces appels, les étapes, c à d, sont répétées. `pOuter` pointe vers le sous-type de projet le plus à l’extérieur `IUnknown` pour chaque niveau d’agrégation.

## <a name="example"></a>Exemple

L’exemple suivant décrit en détail le processus de programmation dans une représentation approximative de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> méthode telle qu’elle est implémentée par l’environnement. Le code n’est qu’un exemple. elle n’est pas destinée à être compilée et toutes les vérifications d’erreurs ont été supprimées pour plus de clarté.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)
