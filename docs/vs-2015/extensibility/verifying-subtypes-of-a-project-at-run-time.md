---
title: Vérification des sous-types d’un projet en cours d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8aa68670b82fdba0f189cfb8bf2a06db15f33b4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215057"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Vérification des sous-types d’un projet au moment de l’exécution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage qui dépend d’un sous-type de projet personnalisé doit inclure une logique à rechercher qui sous-type afin qu’elle peut échouer normalement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.  
  
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
 [Conception de sous-types de projet](../extensibility/internals/project-subtypes-design.md)   
 [Propriétés et méthodes étendues par les sous-types de projets](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

