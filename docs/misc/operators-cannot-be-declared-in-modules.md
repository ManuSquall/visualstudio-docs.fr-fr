---
title: "Les op&#233;rateurs ne peuvent pas &#234;tre d&#233;clar&#233;s dans des modules | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs ne peuvent pas &#234;tre d&#233;clar&#233;s dans des modules
Une [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) s’affiche dans une définition de module.  
  
 Vous pouvez définir un opérateur dans le cadre d’une classe ou d’une structure que vous définissez. L’opérateur doit accepter cette classe ou cette structure comme au moins l’un de ses opérandes.  
  
 Un opérateur doit utiliser une instance d’un élément de programmation comme l’un de ses opérandes, et seules les classes et les structures ont des instances. Vous ne pouvez donc pas définir un opérateur dans le cadre d’un autre élément de programmation.  
  
 **ID d’erreur :** BC33018  
  
### Pour corriger cette erreur  
  
-   Si vous avez besoin d’une opération sur le module, utilisez une [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) pour définir une procédure `Function` qui effectue l’opération.  
  
-   Vous pouvez également définir une classe ou une structure dans le module et définir un opérateur sur cette classe ou structure. Toutefois, cet opérateur doit accepter une instance de cette classe ou structure comme au moins l’un de ses opérandes.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)