---
title: "Exposer des objets de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "objets du projet, exposant"
  - "extensibilité, les objets du projet"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Exposer des objets de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les types de projet personnalisé peuvent fournir des objets automation afin d'autoriser l'accès au projet à l'aide des interfaces d'automatisation. Chaque type de projet est censé fournir la norme <xref:EnvDTE.Project> objet automation qui est accessible à partir de <xref:EnvDTE.Solution>, qui contient une collection de tous les projets ouverts dans l'IDE. Chaque élément dans le projet est prévu pour être exposé par un <xref:EnvDTE.ProjectItem> objet accédé avec <xref:Project.ProjectItems>. En plus de ces objets automation standard, projets peuvent choisir de proposer des objets spécifiques au projet automation.  
  
 Vous pouvez créer des personnalisés au niveau racine objets automation que vous pouvez accéder à liaison tardive à partir de l'objet DTE racine à l'aide `DTE.<customeObjectName>` ou `DTE.GetObject(“<customObjectName>”)`. Par exemple, Visual C\+\+ crée la collection de projet spécifique à un projet C\+\+ appelée « VCProjects » que vous pouvez accéder à l'aide de DTE. VCProjects ou DTE. Par exemple, DTE. Vous pouvez également créer un Project.Object, qui est unique pour le type de projet, un Project.CodeModel, qui peut être interrogé pour son objet ProjectItem qui expose ProjectItem.Object et un ProjectItem.FileCodeModel plus dérivé.  
  
 Il est couramment utilisée pour les projets d'exposer une collection de projets personnalisés, spécifiques à un projet. Par exemple, [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] crée une collection de projets spécifiques de C\+\+ que vous pouvez ensuite accéder à l'aide de `DTE.VCProjects` ou `DTE.GetObject("VCProjects")`. Vous pouvez également créer un `Project.Object`, qui est unique pour le type de projet, un `Project.CodeModel`, qui peuvent être interrogé pour son objet le plus dérivé, un `ProjectItem`, qui expose `ProjectItem.Object`, et un `ProjectItem.FileCodeModel`.  
  
### Contribuer un objet VSPackage spécifique pour un projet  
  
1.  Ajoutez les clés appropriées dans le fichier .pkgdef de votre VSPackage.  
  
     Par exemple, voici les paramètres .pkgdef pour le projet de langage C\+\+ :  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implémentez le code dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode, comme illustré dans l'exemple suivant.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     Dans le code, `g_wszAutomationProjects` est le nom de votre collection de projets. Le `GetAutomationProjects` méthode crée un objet qui implémente le `Projects` interface et retourne un `IDispatch` pointeur vers l'objet appelant, comme illustré dans l'exemple de code suivant.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     Vous devez choisir un nom unique pour votre objet automation. Conflits de noms sont imprévisibles et collisions provoquent un nom d'objet en conflit pour arbitrairement générée si plusieurs types de projets utilisent le même nom. Vous devez inclure le nom de votre société ou un aspect unique de son nom de produit le nom de l'objet automation.  
  
     Personnalisé `Projects` objet de collection est un point d'entrée de commodité pour la partie restante de votre modèle automation de projet. Objet de votre projet est également accessible à partir de la <xref:EnvDTE.Solution> collection de projets. Après avoir créé les entrées appropriées de code et de Registre qui fournissent aux consommateurs `Projects` objets de collection, votre implémentation doit fournir restant objets standard pour le modèle de projet. Pour plus d'informations, consultez [Modélisation de projet](../../extensibility/internals/project-modeling.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>