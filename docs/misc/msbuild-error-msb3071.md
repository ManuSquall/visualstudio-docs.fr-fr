---
title: "MSBuild Error MSB3071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3071
**Toutes les lettres de lecteur depuis A: jusqu'à Z: sont actuellement utilisées.  Le répertoire de travail "'\<chemin d'accès\>'" étant un chemin d'accès UNC, la tâche "Exec" nécessite une lettre de lecteur disponible vers lequel le chemin d'accès UNC sera mappé.  Déconnectez\-vous d'une ou de plusieurs ressources partagées pour libérer des lettres de lecteur ou spécifiez un répertoire de travail local avant de réexécuter cette commande.**  
  
 Toutes les lettres de lecteur depuis A: jusqu'à Z: sont actuellement utilisées.  Le répertoire de travail spécifié étant un chemin d'accès UNC, la tâche `Exec` nécessite une lettre de lecteur disponible sur laquelle mapper le chemin d'accès UNC.  
  
### Pour corriger cette erreur  
  
-   Déconnectez\-vous d'une ou de plusieurs ressources partagées pour libérer certaines lettres de lecteur.  
  
-   Spécifiez un répertoire de travail local avant de tenter à nouveau cette commande.  
  
## Voir aussi  
 [Exec Task](../msbuild/exec-task.md)