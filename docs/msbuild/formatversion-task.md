---
title: "FormatVersion Task | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatVersion Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ajoute le numéro de révision au numéro de version.  
  
-   Case \#1: Input: Version\=\<undefined\>;  Revision\=\<don't care\>;   Output: OutputVersion\="1.0.0.0"  
  
-   Case \#2: Input: Version\="1.0.0.\*"  Revision\="5"  Output: OutputVersion\="1.0.0.5"  
  
-   Case \#3: Input: Version\="1.0.0.0"  Revision\=\<don't care\>;  Output: OutputVersion\="1.0.0.0"  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `FormatVersion`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FormatType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de format.<br /><br /> -   "Version" \= version.<br />-   "Path" \= remplacer "." par "\_";|  
|`OutputVersion`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la version de sortie qui inclut le numéro de révision.|  
|`Revision`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la révision à ajouter à la version.|  
|`Version`|Paramètre `String` facultatif.<br /><br /> Spécifie la chaîne de numéro de version à mettre en forme.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)