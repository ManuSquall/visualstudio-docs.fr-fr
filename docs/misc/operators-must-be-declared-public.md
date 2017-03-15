---
title: "Les op&#233;rateurs doivent &#234;tre d&#233;clar&#233;s &#39;Public&#39; | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs doivent &#234;tre d&#233;clar&#233;s &#39;Public&#39;
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) n’inclut pas le mot clé [Public](/dotnet/visual-basic/language-reference/modifiers/public).  
  
 Une procédure `Operator` exige les deux mots clés `Public` et [Shared](/dotnet/visual-basic/language-reference/modifiers/shared), et un opérateur de conversion nécessite également le mot clé [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou le mot clé [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 **ID d’erreur :** BC33011  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Public` à l’instruction `Operator`.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)