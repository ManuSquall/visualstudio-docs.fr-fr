---
title: "L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir un second param&#232;tre de type &#39;Integer&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir un second param&#232;tre de type &#39;Integer&#39;
Un opérateur de décalage de bits est déclaré avec le deuxième paramètre d’un type autre que `Integer`.  
  
 Quand vous utilisez l’opérateur de décalage vers la droite \(`>>`\) ou vers la gauche \(`<<`\) dans une expression, vous spécifiez le nombre de positions de décalage dans le second opérande. Pour cet opérande, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vous permet de fournir un type de données qui s’étend à `Integer`. Toutefois, la définition du second opérande est strictement `Integer`. Si vous définissez une classe ou une structure avec un opérateur de décalage de bits sur cette classe ou structure, votre définition doit spécifier `Integer` pour le second opérande.  
  
 **ID d’erreur :** BC33041  
  
### Pour corriger cette erreur  
  
-   Modifiez la définition de l’opérateur de décalage de bits pour retourner une valeur `Integer`.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Bit Shift Operators](/dotnet/visual-basic/language-reference/operators/bit-shift-operators)