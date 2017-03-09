---
title: "L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir un type de retour Boolean. | Microsoft Docs"
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
  - "vbc33023"
  - "bc33023"
helpviewer_keywords: 
  - "BC33023"
ms.assetid: 18e066f4-d71e-4e38-b0bc-8af9145f6015
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir un type de retour Boolean.
Un opérateur de comparaison ou logique est déclaré avec un autre type de retour que [Boolean Data Type](/dotnet/visual-basic/language-reference/data-types/boolean-data-type).  
  
 Le résultat d’un opérateur de comparaison \(`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `IsFalse`, `IsTrue`, `Like`, `TypeOf`\) ne peut être que `True` ou `False`. Pour plus d'informations, consultez [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators).  
  
 Les opérateurs logiques \(`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`\) fonctionnent entièrement dans le domaine des valeurs booléennes. Pour plus d'informations, consultez [Logical and Bitwise Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators).  
  
 **ID d’erreur :** BC33023  
  
### Pour corriger cette erreur  
  
-   Remplacez le type de retour de cet opérateur de comparaison ou logique par `Boolean`.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)