---
title: "Un caract&#232;re de type ne peut pas &#234;tre utilis&#233; dans une d&#233;claration &#39;Sub&#39;, car un &#39;Sub&#39; ne retourne pas de valeur | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un caract&#232;re de type ne peut pas &#234;tre utilis&#233; dans une d&#233;claration &#39;Sub&#39;, car un &#39;Sub&#39; ne retourne pas de valeur
Une procédure `Sub`, comme une procédure `Function`, est une procédure distincte qui peut accepter des arguments et exécuter une série d’instructions. Contrairement à une procédure `Function`, une procédure `Sub` ne retourne pas de valeur et ne peut donc pas contenir de déclaration de type.  
  
 **ID d’erreur :** BC30303  
  
### Pour corriger cette erreur  
  
-   Remplacez la procédure `Sub` par une procédure `Function`.  
  
## Voir aussi  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function, procédures](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)