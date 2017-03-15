---
title: "L’option Strict On interdit les op&#233;randes de type Object pour l’op&#233;rateur &#39;&lt;nom_op&#233;rateur&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’option Strict On interdit les op&#233;randes de type Object pour l’op&#233;rateur &#39;&lt;nom_op&#233;rateur&gt;&#39;
L’option Strict On interdit les opérandes de type Object pour l’opérateur '\<nom\_opérateur\>'. Utilisez l’opérateur Is pour tester l’identité de l’objet.  
  
 Un opérateur de comparaison arithmétique comme `=` est utilisé avec une ou plusieurs variables d’objet quand `Option Strict` a la valeur `On`.  
  
 **ID d’erreur :** BC32013  
  
### Pour corriger cette erreur  
  
1.  Activez `Option Strict Off` si les variables d’objet contiennent des valeurs numériques et que vous voulez effectuer une comparaison arithmétique.  
  
2.  Utilisez l’opérateur `Is` pour comparer l’identité de l’objet.  
  
## Voir aussi  
 [Comparison Operators](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)