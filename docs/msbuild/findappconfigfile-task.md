---
title: "FindAppConfigFile Task | Microsoft Docs"
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
  - "FindAppConfigFile task [MSBuild]"
  - "MSBuild, FindAppConfigFile task"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FindAppConfigFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recherche le fichier app.config, le cas échéant, dans les listes fournies.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `FindAppConfigFile`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AppConfigFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le premier élément correspondant trouvé dans la liste, le cas échéant.|  
|`PrimaryList`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste principale dans laquelle effectuer la recherche.|  
|`SecondaryList`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la liste secondaire dans laquelle effectuer la recherche.|  
|`TargetPath`|Paramètre `String` obligatoire.<br /><br /> Spécifie la valeur à ajouter en tant que métadonnées.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)