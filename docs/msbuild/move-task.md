---
title: "Move Task | Microsoft Docs"
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
  - "MSBuild, Move task"
  - "Move task [MSBuild]"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Move Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Déplace les fichiers vers un nouvel emplacement.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `Move`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`DestinationFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie la liste des fichiers vers laquelle déplacer les fichiers sources.  Cette liste représente en principe un mappage un à un avec la liste spécifiée dans le paramètre `SourceFiles`.  En d'autres termes, le premier fichier spécifié dans `SourceFiles` est déplacé vers le premier emplacement spécifié dans `DestinationFiles`, et ainsi de suite.|  
|`DestinationFolder`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le répertoire vers lequel vous souhaitez déplacer les fichiers.|  
|`MovedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments dont le déplacement a réussi.|  
|`OverwriteReadOnlyFiles`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, cela écrase les fichiers même s'ils sont marqués comme fichiers en lecture seule.|  
|`SourceFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à déplacer.|  
  
## Notes  
 Le paramètre `DestinationFolder` ou `DestinationFiles` doit être spécifié, mais pas les deux.  Si les deux sont spécifiés, la tâche échoue et une erreur est consignée.  
  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)