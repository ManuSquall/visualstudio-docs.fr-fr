---
title: "&#39;Sub&#39; ou &#39;Function&#39; attendu apr&#232;s &#39;Delegate&#39; | Microsoft Docs"
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
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub&#39; ou &#39;Function&#39; attendu apr&#232;s &#39;Delegate&#39;
Une instruction `Delegate` ne spécifie pas une procédure `Sub` ou `Function`. Le mot clé `Sub` ou `Function` doit suivre immédiatement le mot clé `Delegate`.  
  
 **ID d’erreur :** BC30278  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le mot clé `Sub` ou `Function` immédiatement après `Delegate`.  
  
2.  Spécifiez un nom de procédure, une liste d’arguments et un type de retour selon vos besoins.  
  
## Voir aussi  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)