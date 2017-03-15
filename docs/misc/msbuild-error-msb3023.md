---
title: "MSBuild Error MSB3023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3023
**Aucune destination spécifiée pour l'opération de copie.  Indiquez "'\<attribut\>'" ou "'\<attribut\>'".**  
  
 Une destination doit être spécifiée pour la tâche `Copy` à l'aide de l'un des attributs de tâche `DestinationFiles`et`DestinationDirectory`.  
  
### Pour corriger cette erreur  
  
-   Spécifiez `DestinationFiles`ou`DestinationDirectory`pour la tâche `Copy`.  
  
## Voir aussi  
 [Copy Task](../msbuild/copy-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)