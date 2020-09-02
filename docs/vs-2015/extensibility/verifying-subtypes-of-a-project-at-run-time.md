---
title: Vérification des sous-types d’un projet au moment de l’exécution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584903"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Vérification des sous-types d’un projet au moment de l’exécution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage qui dépend d’un sous-type de projet personnalisé doit inclure une logique pour rechercher ce sous-type afin qu’il puisse échouer correctement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Pour vérifier la présence d’un sous-type  
  
1. Obtenez la hiérarchie de projet à partir des objets projet et solution en tant qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet en ajoutant le code suivant à votre VSPackage.  
  
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
  
2. Effectuez un cast de la hiérarchie en <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Obtient la liste des GUID de type de projet en appelant <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Vérifiez la liste du GUID du sous-type spécifié.  
  
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
 [Conception de sous-types de projet](../extensibility/internals/project-subtypes-design.md)   
 [Propriétés et méthodes étendues par les sous-types de projets](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
