---
title: "Les op&#233;rateurs de conversion doivent &#234;tre d&#233;clar&#233;s &#39;Widening&#39; ou &#39;Narrowing&#39; | Microsoft Docs"
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
  - "vbc33017"
  - "bc33017"
helpviewer_keywords: 
  - "BC33017"
ms.assetid: 5972d955-ce1d-4348-a021-167eecb3a507
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs de conversion doivent &#234;tre d&#233;clar&#233;s &#39;Widening&#39; ou &#39;Narrowing&#39;
Une instruction [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) ne spécifie pas [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ni [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Quand vous définissez un opérateur de conversion, vous devez le déclarer comme `Widening` ou `Narrowing`. Ces caractéristiques étant mutuellement exclusives, vous ne pouvez pas spécifier les deux.  
  
 **ID d’erreur :** BC33017  
  
### Pour corriger cette erreur  
  
-   Choisissez si l’opérateur de conversion doit être `Widening` ou `Narrowing`, et incluez le mot clé approprié dans l’instruction `Operator`. Vous devez spécifier l’un ou l’autre.  
  
## Voir aussi  
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)