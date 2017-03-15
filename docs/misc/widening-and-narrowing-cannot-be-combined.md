---
title: "&#39;Widening&#39; et &#39;Narrowing&#39; ne peuvent pas &#234;tre combin&#233;s | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Widening&#39; et &#39;Narrowing&#39; ne peuvent pas &#234;tre combin&#233;s
Une [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) spécifie à la fois [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) et [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Quand vous définissez un opérateur de conversion, vous devez le déclarer comme `Widening` ou `Narrowing`. Ces caractéristiques étant mutuellement exclusives, vous ne pouvez pas spécifier les deux.  
  
 **ID d’erreur :** BC33001  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Widening` ou `Narrowing` de l’instruction `Operator`. Vous devez spécifier l’un ou l’autre.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)