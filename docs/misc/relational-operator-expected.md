---
title: "Op&#233;rateur relationnel attendu | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#233;rateur relationnel attendu
Une instruction `Case` contient une clause `Is` mais aucun opérateur de comparaison tel que `=` ou `>`. Si une instruction `Case` ne comporte pas d’opérateur, `=` est adopté par défaut et `Is` n’est pas utilisé.  
  
 **ID d’erreur :** BC30239  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Is` ou faites\-le suivre d’un opérateur de comparaison.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Comparison Operators](/dotnet/visual-basic/language-reference/operators/comparison-operators)