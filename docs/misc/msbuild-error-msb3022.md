---
title: "MSBuild Error MSB3022 | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3022
**"'\<attribut\>'" et "'\<attribut\>'" ont tous les deux été spécifiés comme paramètres d'entrée dans le fichier projet.  Choisissez l'un ou l'autre.**  
  
 Pour la tâche `Copy`, vous devez spécifier `DestinationFiles` ou `DestinationDirectory`, mais pas les deux attributs à la fois.  
  
### Pour corriger cette erreur  
  
-   Spécifiez `DestinationFiles` ou `DestinationDirectory` pour la tâche `Copy` du fichier projet.  
  
## Voir aussi  
 [Copy Task](../msbuild/copy-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)