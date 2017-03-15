---
title: "ResolveNonMSBuildProjectOutput Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveNonMSBuildProjectOutput task"
  - "ResolveNonMSBuildProjectOutput task [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResolveNonMSBuildProjectOutput Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détermine les fichiers de sortie pour les références de projet non MSBuild.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `ResolveNonMSBuildProjectOutput`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne XML contenant les sorties de projet résolues.|  
|`ProjectReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]`  obligatoire.<br /><br /> Spécifie les références du projet.|  
|`ResolvedOutputPaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste de chemins d'accès de référence résolus \(et conserve les attributs de référence de projet d'origine\).|  
|`UnresolvedProjectReferences`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments de référence de projet qui n'ont pas pu être résolus à l'aide de la liste de sorties pré\-résolue.<br /><br /> Dans la mesure où Visual Studio prérésout seulement les projets non MSBuild, cela signifie que les références de projet dans cette liste sont au format MSBuild.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)