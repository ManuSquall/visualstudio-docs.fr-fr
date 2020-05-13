---
title: Séquence d’initialisation des sous-types de projets (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707629"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Séquence d’initialisation des sous-types de projets
L’environnement construit un projet en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>la mise en œuvre de l’usine de projet de base de . La construction d’un sous-type de projet commence lorsque l’environnement détermine que la liste GUID de type projet pour l’extension d’un fichier de projet n’est pas vide. L’extension du fichier du projet et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet GUID précisent si le projet est un type de projet ou de projet. Par exemple, l’extension .vbproj et le F184B08F-C81C-45F6-A57F-5ABD9991F28F28F' identifient un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisation des sous-types de projets par environnement
 La procédure suivante détaille la séquence d’initialisation d’un système de projet agrégé par plusieurs sous-types de projets.

1. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>projet de base , et tandis que le projet analyse son dossier de `null`projet, il découvre que la liste de type de projet agrégé GUIDs n’est pas . Le projet cesse de créer directement son projet.

2. Le projet `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> fait appel à un service pour créer un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> sous-type de projet utilisant la mise en œuvre de la méthode par l’environnement. Dans cette méthode, l’environnement fait des appels <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> fonction récursifs à vos implémentations de , et les méthodes pendant qu’il marche la liste des GUIDs de type projet, en commençant par le sous-type de projet le plus externe.

     Les détails suivants les étapes d’initialisation.

    1. La mise en œuvre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> méthode par l’environnement appelle la `HrCreateInnerProj` méthode avec la déclaration de fonction suivante :

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Lorsque cette fonction est appelée pour la première fois, c’est-à-dire, pour le sous-type de projet le plus externe, les paramètres `pOuter` et `pOwner` sont transmis en tant que `null` et la fonction définit le sous-type `IUnknown` de projet le plus externe à `pOuter`.

    2. Ensuite, l’environnement appelle `HrCreateInnerProj` la fonction avec le deuxième type de projet GUID dans la liste. Ce GUID correspond au deuxième sous-type de projet intérieur entrant vers le projet de base dans la séquence d’agrégation.

    3. Le `pOuter` est maintenant `IUnknown` pointant vers le sous-type `HrCreateInnerProj` de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> le plus externe, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>et appelle votre mise en œuvre suivie d’un appel à votre mise en œuvre de . Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> la méthode que vous `IUnknown` passez dans le contrôle `pOuter`du sous-type de projet le plus externe, . Le projet possédé (sous-type de projet intérieur) doit créer ici son objet de projet agrégé. Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> la mise en œuvre `IUnknown` de la méthode, vous passez dans un pointeur du projet intérieur qui est en cours d’agrégation. Ces deux méthodes créent l’objet d’agrégation, et vos implémentations doivent suivre les règles d’agrégation com pour s’assurer qu’un sous-type de projet ne finit pas par tenir un compte de référence à lui-même.

    4. `HrCreateInnerProj`appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>mise en œuvre de . Dans cette méthode, le sous-type de projet effectue son travail d’initialisation. Vous pouvez, par exemple, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>enregistrer les événements de solution dans .

    5. `HrCreateInnerProj`est appelé récursivement jusqu’à ce que le dernier GUID (le projet de base) dans la liste est atteint. Pour chacun de ces appels, les étapes, c à travers d, sont répétées. `pOuter`pointe vers le sous-type `IUnknown` de projet le plus externe pour chaque niveau d’agrégation.

## <a name="example"></a>Exemple

L’exemple suivant détaille le processus programmatique dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> une représentation approximative de la méthode telle qu’elle est mise en œuvre par l’environnement. Le code n’est qu’un exemple; il n’est pas destiné à être compilé, et toute vérification des erreurs a été supprimée pour plus de clarté.

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
