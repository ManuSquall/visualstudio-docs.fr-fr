---
title: "MSBuild Error MSB1012 | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1012
**Spécifier un fichier réponse.**  
  
 Un fichier réponse doit être spécifié pour le @ commutateur.  
  
### Pour corriger cette erreur  
  
-   Spécifier un fichier réponse.  La syntaxe est @\<nom fichier\>, par exemple, `@BuildHW.txt`  
  
-   N'incluez pas le @ commutateur sur la ligne de commande.  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)