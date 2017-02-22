---
title: "ConvertToAbsolutePath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ConvertToAbsolutePath task [MSBuild]"
  - "MSBuild, ConvertToAbsolutePath task"
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# ConvertToAbsolutePath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Convertit un chemin d'accès relatif ou une référence en chemin d'accès absolu.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `ConvertToAbsolutePath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Paths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste des chemins d'accès relatifs à convertir en chemins d'accès absolus.|  
|`AbsolutePaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Liste des chemins d'accès absolus pour les éléments passés.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)