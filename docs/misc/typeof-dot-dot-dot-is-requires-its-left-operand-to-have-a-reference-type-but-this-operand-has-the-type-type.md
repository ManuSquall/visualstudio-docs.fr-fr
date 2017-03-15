---
title: "&#39;TypeOf ... Is&#39; requiert un op&#233;rande gauche ayant un type r&#233;f&#233;rence, mais cet op&#233;rande a le type valeur &#39;&lt;type&gt;&#39; | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TypeOf ... Is&#39; requiert un op&#233;rande gauche ayant un type r&#233;f&#233;rence, mais cet op&#233;rande a le type valeur &#39;&lt;type&gt;&#39;
L’expression `TypeOf...Is` vérifie la compatibilité de type au moment de l’exécution d’une variable objet. Cette compatibilité n’est pas définie pour les types valeur.  
  
 **ID d’erreur :** BC30021  
  
### Pour corriger cette erreur  
  
-   Si `Option Strict` est `Off`, utilisez la fonction `TypeName` ou `VarType` pour obtenir les informations de type de données sur la variable.  
  
-   Si `Option Strict` est `On`, la déclaration de variable détermine le type de données de la variable.  
  
## Voir aussi  
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [NOT IN BUILD : TypeName, fonction \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [NOT IN BUILD : VarType, fonction \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)