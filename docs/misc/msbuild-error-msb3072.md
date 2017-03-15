---
title: "MSBuild Error MSB3072 | Microsoft Docs"
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
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3072
**La tâche "Exec" nécessite une commande pour s'exécuter.**  
  
 L'attribut `Command` est un attribut requis pour la tâche `Exec`.  
  
### Pour corriger cette erreur  
  
1.  Dans le fichier projet, spécifiez l'attribut `Command` pour la tâche `Exec`.  
  
## Voir aussi  
 [Exec Task](../msbuild/exec-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)