---
title: "&#39;Handles&#39; n’est pas valide pour la d&#233;claration d’op&#233;rateur | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; n’est pas valide pour la d&#233;claration d’op&#233;rateur
Une [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) spécifie le mot clé [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause).  
  
 Seule une procédure `Sub` peut gérer des événements. Une procédure `Operator` ne le peut pas. Pour plus d’informations sur les gestionnaires d’événements, consultez [How to: Call an Event Handler in Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md).  
  
 Une procédure `Operator` exige les deux mots clés `Public` et `Shared`, et un opérateur de conversion nécessite le mot clé `Widening` ou le mot clé `Narrowing`. Pour plus d'informations, consultez [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **ID d’erreur :** BC33003  
  
### Pour corriger cette erreur  
  
-   Si cette procédure doit gérer des événements, réécrivez\-la en tant que procédure `Sub`.  
  
-   Si cette procédure doit définir un opérateur, supprimez le mot clé `Handles` de sa déclaration.  
  
## Voir aussi  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)