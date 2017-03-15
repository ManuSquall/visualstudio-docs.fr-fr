---
title: "MSBuild Error MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1002
**Ce commutateur ne prend pas de paramètres.**  
  
 Il n'est pas possible de définir des paramètres pour ce commutateur.  Seul le nom du commutateur est requis et il ne doit pas être suivi par un signe deux\-points \(:\).  
  
### Pour corriger cette erreur  
  
-   Tapez la commande sans aucun paramètre pour ce commutateur – autrement dit, au lieu de taper `msbuild /<switch>:<parameters>`, tapez `msbuild /<switch>`  
  
-   Supprimez le signe deux points \(:\) après le nom du commutateur – autrement dit, au lieu de taper `msbuild /<switch>:`, tapez `msbuild /<switch>`  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)