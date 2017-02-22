---
title: "FormatUrl Task | Microsoft Docs"
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
  - "MSBuild, FormatUrl task"
  - "FormatUrl task [MSBuild]"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatUrl Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Convertit une URL en un format d'URL correct.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `FormatUrl`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`InputUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l'URL à mettre en forme.|  
|`OutputUrl`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l'URL mise en forme.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)