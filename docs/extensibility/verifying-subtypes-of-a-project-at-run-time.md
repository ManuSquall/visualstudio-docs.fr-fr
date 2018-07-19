---
title: Vérification des sous-types d’un projet au moment de l’exécution | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8898da6850c01c1a248b57b0fbc5f46be2a8ff4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136827"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Vérification des sous-types d’un projet au moment de l’exécution
Un VSPackage qui dépend d’un sous-type de projet personnalisé doit inclure une logique à rechercher qui sous-type afin qu’elle peut échouer correctement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Pour vérifier la présence d’un sous-type  
  
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
  
2.  Effectuer un cast de la hiérarchie pour le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obtenir la liste des GUID de type de projet en appelant le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Vérifiez la liste pour le GUID du sous-type spécifié.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Sous-types de projet](../extensibility/internals/project-subtypes.md)   
 [Conception des sous-types de projet](../extensibility/internals/project-subtypes-design.md)   
 [Propriétés et méthodes étendues par les sous-types de projets](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)