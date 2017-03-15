---
title: "S&#233;quence d&#39;initialisation des sous-types de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sous-types de projets, séquence d'initialisation"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# S&#233;quence d&#39;initialisation des sous-types de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

l'environnement construit un projet en appelant l'implémentation de base de fabrique de projet de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>.  La construction d'un sous\-type de projet lorsque l'environnement détermine que la liste des GUID de type de projet pour une extension de fichier projet n'est pas vide.  l'extension et le GUID du projet de fichier projet spécifient si le projet est un type de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou de projet csprcs.  Par exemple, l'extension .vbproj et {F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F} identifient un projet de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## l'initialisation de l'environnement des sous\-types de projet  
 La procédure suivante détaille la séquence d'initialisation d'un système de projet forme par plusieurs sous\-types de projet.  
  
1.  L'environnement appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>de base du projet, et pendant que le projet analyse son fichier projet il détecte que la liste globale de GUID de type de projet n'est pas `null`.  Le projet arrête de créer directement son projet.  
  
2.  Le projet appelle `QueryService` sur le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> pour créer un sous\-type de projet en utilisant l'implémentation de l'environnement de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> .  Dans cette méthode l'environnement effectue des appels de fonction récursive à vos implémentations d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, d' `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` et des méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> pendant qu'il parcourt la liste de type GUID du projet, en commençant par le sous\-type extérieur de projet.  
  
     Les informations suivantes les étapes d'initialisation.  
  
    1.  l'implémentation de l'environnement de la méthode d' `HrCreateInnerProj```d'appels de méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> avec la déclaration de fonction suivante :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Lorsque cette fonction est appelée pour la première fois, c. autrement dit., pour le sous\-type extérieur de projet, les paramètres `pOuter` et `pOwner` sont passés comme `null` et la fonction définit le sous\-type extérieur `IUnknown` de projet à `pOuter`.  
  
    2.  Suivant la fonction d' `HrCreateInnerProj` d'appels d'environnement avec le second type GUID du projet dans la liste.  Ce GUID correspond au deuxième sous\-type interne de projet intermédiaire vers le projet de base de la séquence de regroupement.  
  
    3.  `pOuter` pointe désormais vers `IUnknown` de sous\-type extérieur de projet, et les appels d' `HrCreateInnerProj` que votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> a suivis par un appel à l'implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>.  Dans la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> vous passez `IUnknown` contrôlant de sous\-type extérieur de projet, `pOuter`.  Les besoins détenus de projet \(sous\-type interne de projet\) de créer son objet global de projet ici.  Dans l'implémentation de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> vous passez un pointeur à `IUnknown` du projet interne qui est regroupé.  Ces deux méthodes créent l'objet de regroupement, et vos implémentations doivent suivre les règles de regroupement COM pour garantir qu'un sous\-type de projet ne se termine pas maintenant un décompte de références à lui\-même.  
  
    4.  `HrCreateInnerProj` appelle votre implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>.  dans cette méthode, le sous\-type de projet effectue son travail d'initialisation.  Vous pouvez, par exemple, enregistrer les événements de solution dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj` est appelée de manière récursive jusqu'à ce que dernier GUID \(le projet de base\) dans la liste soit atteint.  pour chacun de ces appels, les étapes, c à d, sont répétées.  points d'`pOuter` au sous\-type extérieur `IUnknown` de projet pour chaque niveau de regroupement.  
  
 L'exemple suivant détaille le processus de programmation dans une représentation approximative de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> à mesure qu'il est implémenté par l'environnement.  Le code est simplement un exemple ; il n'est pas prévu pour être compilé et toute la vérification des erreurs a été supprimée de clarté.  
  
## Exemple  
  
### Code  
  
```  
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
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Sous\-types de projets](../../extensibility/internals/project-subtypes.md)