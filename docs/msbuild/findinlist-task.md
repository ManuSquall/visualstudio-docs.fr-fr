---
title: "FindInList Task | Microsoft Docs"
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
  - "FindInList task [MSBuild]"
  - "MSBuild, FindInList task"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# FindInList Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans une liste spécifiée, recherche un élément associé à la spécification d'éléments \(itemspec\) correspondante.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche [FindInList Task](../msbuild/findinlist-task.md).  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`CaseSensitive`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la recherche respecte la casse et dans le cas contraire, elle ne la respecte pas.  La valeur par défaut est `true`|  
|`FindLastMatch`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, retournez la dernière correspondance, sinon, retournez la première correspondance.  La valeur par défaut est `false`|  
|`ItemFound`|Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Premier élément correspondant trouvé dans la liste, le cas échéant.|  
|`ItemSpecToFind`|Paramètre `String` obligatoire.<br /><br /> Spécification d'éléments \(itemspec\) à rechercher.|  
|`List`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste dans laquelle rechercher la spécification d'éléments \(itemspec\).|  
|`MatchFileNameOnly`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, établissez une correspondance avec une portion du nom de fichier de la spécification d'éléments \(itemspec\), sinon établissez une correspondance avec la spécification d'éléments \(itemspec\) entière.  La valeur par défaut est `true`|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)