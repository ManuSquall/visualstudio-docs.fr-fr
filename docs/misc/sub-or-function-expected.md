---
title: "&#39;Sub&#39; ou &#39;Function&#39; attendu | Microsoft Docs"
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
  - "vbc30215"
  - "bc30215"
helpviewer_keywords: 
  - "BC30215"
ms.assetid: 013f4200-b3cf-4cd8-a235-15067ca773fc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub&#39; ou &#39;Function&#39; attendu
Une instruction `Declare` ne spécifie pas `Sub` ou `Function`.`Declare` identifie une procédure externe et doit spécifier le type de procédure.  
  
 **ID d’erreur :** BC30215  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Sub` ou `Function` à l’instruction `Declare`.  
  
## Voir aussi  
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)