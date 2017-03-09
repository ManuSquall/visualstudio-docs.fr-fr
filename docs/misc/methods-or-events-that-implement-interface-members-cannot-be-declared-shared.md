---
title: "Les m&#233;thodes ou &#233;v&#233;nements qui impl&#233;mentent des membres d’interface ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;Shared&#39; | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes ou &#233;v&#233;nements qui impl&#233;mentent des membres d’interface ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;Shared&#39;
Vous avez tenté de déclarer en tant que `Shared` une méthode ou un événement qui implémente un membre d’interface. Les méthodes et les événements implémentés dans une classe ne peuvent pas être désignés comme `Shared` ou `Private`, sauf dans une classe non héritable.  
  
 **ID d’erreur :** BC30505  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Shared`.  
  
## Voir aussi  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)