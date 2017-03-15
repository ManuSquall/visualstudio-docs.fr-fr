---
title: "Les instructions &#39;GoTo&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution | Microsoft Docs"
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
  - "bc30133"
  - "vbc30133"
helpviewer_keywords: 
  - "BC30133"
ms.assetid: e5901616-6aec-4718-b452-90b2143301b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;GoTo&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution
L’instruction `GoTo` procède à une création de branche et n’est pas autorisée dans un contexte de débogage.  
  
 **ID d’erreur :** BC30133  
  
### Pour corriger cette erreur  
  
-   N’émettez pas d’instruction `GoTo` dans la fenêtre **Exécution**.  
  
## Voir aussi  
 [Fenêtre Exécution](../ide/reference/immediate-window.md)