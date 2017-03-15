---
title: "La cr&#233;ation d’une branche en dehors d’un &#39;Finally&#39; n’est pas valide | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La cr&#233;ation d’une branche en dehors d’un &#39;Finally&#39; n’est pas valide
Une instruction `GoTo` comprise dans un bloc `Finally` crée une branche en dehors du bloc. Il n’est pas possible de créer une branche à l’intérieur ou à l’extérieur d’un bloc `Catch` ou `Finally`.  
  
 **ID d’erreur :** BC30101  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `GoTo`, puis implémentez la logique du programme avec des structures de contrôle de boucle ou de décision.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Control Flow](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)