---
title: "La variable de contr&#244;le &#39;Next&#39; ne correspond pas &#224; la variable de contr&#244;le de boucle &#39;For&#39; | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de contr&#244;le &#39;Next&#39; ne correspond pas &#224; la variable de contr&#244;le de boucle &#39;For&#39;
La variable de contrôle dans l’instruction `Next` d’une boucle `For...Next` doit correspondre à la variable dans l’instruction `For` correspondante.  
  
 **ID d’erreur :** BC30976  
  
### Pour corriger cette erreur  
  
-   Vérifiez l’orthographe de la variable dans l’instruction `Next` et dans l’instruction `For` correspondante pour être certain qu’elle concorde.  
  
-   Vérifiez qu’aucune partie de la boucle englobante n’a été supprimée par inadvertance.  
  
-   Si cette boucle fait partie d’un ensemble de boucles imbriquées, vérifiez que chaque boucle se termine correctement.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)