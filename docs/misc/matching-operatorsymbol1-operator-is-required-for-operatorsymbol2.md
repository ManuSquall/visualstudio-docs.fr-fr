---
title: "Un op&#233;rateur &#39;&lt;symbole_op&#233;rateur1&gt;&#39; correspondant est requis pour &#39;&lt;symbole_op&#233;rateur2&gt;&#39; | Microsoft Docs"
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
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un op&#233;rateur &#39;&lt;symbole_op&#233;rateur1&gt;&#39; correspondant est requis pour &#39;&lt;symbole_op&#233;rateur2&gt;&#39;
Un opérateur est défini, mais l’opérateur correspondant requis n’est pas défini.  
  
 Les opérateurs suivants doivent être définis comme des paires correspondantes :  
  
-   `=` et `<>`  
  
-   `>` et `<`  
  
-   `>=` et `<=`  
  
-   `IsTrue` et `IsFalse`  
  
 Si vous définissez l’un de ces opérateurs dans une classe ou une structure, vous devez également définir leurs opérateurs correspondants dans cette même classe ou structure.  
  
 Même si vous n’utilisez pas l’opérateur correspondant explicitement, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] peut en avoir besoin. Par exemple, si vous définissez une classe ou une structure que vous utilisez comme variable de compteur dans une [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aura besoin des opérateurs `>=` et `<=` \(ainsi que de l’opérateur `+`\).  
  
 **ID d’erreur :** BC33033  
  
### Pour corriger cette erreur  
  
-   Définissez l’opérateur correspondant dans la même classe ou structure. Définissez\-le de la manière la plus significative possible, car [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pourra l’utiliser dans une situation que vous n’aurez pas anticipée.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operators and Expressions](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)