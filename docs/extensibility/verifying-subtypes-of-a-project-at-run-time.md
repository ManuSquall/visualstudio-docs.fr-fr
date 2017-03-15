---
title: "V&#233;rification des sous-types d’un projet en cours d’ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sous-types de projets"
  - "Vérifiez les sous-types"
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# V&#233;rification des sous-types d’un projet en cours d’ex&#233;cution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un VSPackage qui dépend d’un sous\-type de projet personnalisé doit inclure une logique pour rechercher qui sous\-type afin qu’elle peut échouer correctement si le sous\-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous\-type spécifié.  
  
### Pour vérifier la présence d’un sous\-type  
  
1.  Obtenir la hiérarchie de projet à partir des objets en tant que projet et solution un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet en ajoutant le code suivant à votre VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Effectuer un cast de la hiérarchie vers le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obtenir la liste des GUID de type de projet en appelant le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Vérifiez la liste du GUID du sous\-type spécifié.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## Voir aussi  
 [Sous\-types de projets](../extensibility/internals/project-subtypes.md)   
 [Conception des sous\-types de projet](../extensibility/internals/project-subtypes-design.md)   
 [Propriétés et méthodes étendus par les sous\-types de projets](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)