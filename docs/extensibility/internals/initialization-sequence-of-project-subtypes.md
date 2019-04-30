---
title: Séquence d’initialisation des sous-types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0e42f80485aab478e3739aedb42130699a963ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909690"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Séquence d’initialisation des sous-types de projets
L’environnement construit un projet en appelant l’implémentation de fabrique de projet de base de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. La construction d’un sous-type de projet démarre lorsque l’environnement détermine que la liste GUID de type de projet pour l’extension d’un fichier de projet n’est pas vide. L’extension de fichier de projet et le GUID du projet spécifient si le projet est un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] type de projet. Par exemple, l’extension .vbproj et {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifier un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisation de l’environnement de sous-types de projet
 La procédure suivante décrit en détail la séquence d’initialisation pour un système de projet agrégé par plusieurs sous-types de projet.

1. L’environnement appelle le projet de base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, et pendant que le projet analyse son fichier de projet qu’il découvre que la liste de GUID de type de projet d’agrégation n’est pas `null`. Le projet interrompt la création directe de son projet.

2. Les appels de projet `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> service afin de créer un sous-type de projet à l’aide de la mise en oeuvre de l’environnement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> (méthode). Dans cette méthode, l’environnement, les appels de fonction récursive à vos implémentations de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> GUID, en commençant par le sous-type de projet plus externe du type de méthodes pendant qu’il est de parcourir la liste de projet.

     Les sections suivantes décrivent les étapes d’initialisation.

    1. Implémentation de l’environnement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> les appels de méthode le `HrCreateInnerProj` méthode avec la déclaration de fonction suivante :

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Lorsque cette fonction est appelée pour la première fois, autrement dit, pour le sous-type de projet externe, les paramètres `pOuter` et `pOwner` sont passés comme `null` et la fonction définit le sous-type de projet extérieur `IUnknown` à `pOuter`.

    2. Ensuite, l’environnement appelle `HrCreateInnerProj` fonction avec le deuxième type de projet GUID dans la liste. Ce GUID correspond à la deuxième sous-type de projet interne pas à pas détaillé vers le projet de base dans la séquence d’agrégation.

    3. Le `pOuter` pointent désormais vers le `IUnknown` du sous-type de projet extérieur, et `HrCreateInnerProj` appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> suivie d’un appel à votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> méthode que vous passez dans le contrôle `IUnknown` du sous-type de projet extérieur, `pOuter`. Le projet détenu (sous-type de projet interne) doit créer son objet de projet d’agrégation ici. Dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implémentation de méthode que vous passez un pointeur vers le `IUnknown` du projet interne qui est en cours d’agrégation. Ces deux méthodes créent l’objet d’agrégation et vos implémentations doivent suivre les règles d’agrégation COM pour vous assurer qu’un sous-type de projet ne finit pas maintenir un décompte de références à elle-même.

    4. `HrCreateInnerProj` appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Dans cette méthode, le sous-type de projet effectue son travail d’initialisation. Vous pouvez, par exemple, inscrire des événements de solution dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5. `HrCreateInnerProj` est appelée de manière récursive jusqu'à ce que le dernier GUID (le projet de base) dans la liste est atteint. Pour chacun de ces appels, les étapes, c et d, sont répétés. `pOuter` pointe vers le sous-type de projet extérieur `IUnknown` pour chaque niveau d’agrégation.

## <a name="example"></a>Exemple

L’exemple suivant décrit en détail le processus de programmation dans une représentation approximative de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> de la méthode est implémentée par l’environnement. Le code est juste un exemple ; Il n’est pas destinée à être compilé et toutes les vérifications des erreurs a été supprimé par souci de clarté.

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