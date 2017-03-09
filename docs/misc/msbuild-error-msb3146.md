---
title: "MSBuild Error MSB3146 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3146
**MSB3146 : L'élément '\<package\>' est requis par '\<package\>', mais il n'a pas été inclus.**  
  
 Cette erreur se produit lorsqu'un package de programme d'amorçage dépend d'un autre package, mais vous avez choisi d'installer uniquement le package dépendant.  Par exemple, le package B dépend du package A, mais seul le package B est installé.  
  
### Pour corriger cette erreur  
  
-   Incluez le package requis.