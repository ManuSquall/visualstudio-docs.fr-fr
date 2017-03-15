---
title: "Les arguments nomm&#233;s ne sont pas valides en tant qu’indices de tableau | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments nomm&#233;s ne sont pas valides en tant qu’indices de tableau
Un index de tableau est spécifié à l’aide de la syntaxe nécessaire pour passer un argument de procédure par nom, par exemple `Array(Index := 10)`. Cette syntaxe n’est pas valide pour les indices de tableau.  
  
 **ID d’erreur :** BC30075  
  
### Pour corriger cette erreur  
  
-   Utilisez une variable ordinaire ou une expression constante comme index de tableau, par exemple `Array(10)`.  
  
## Voir aussi  
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)