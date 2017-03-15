---
title: "Les instructions &#39;Return&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution | Microsoft Docs"
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
  - "bc30147"
  - "vbc30147"
helpviewer_keywords: 
  - "BC30147"
ms.assetid: ed3647ce-1450-4c60-96c6-2bfe49cf62d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Return&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution
L’instruction `Return` procède à une création de branches et n’est pas autorisée dans un contexte de débogage.  
  
 **ID d’erreur :** BC30147  
  
### Pour corriger cette erreur  
  
-   N’émettez pas d’instruction `Return` dans la fenêtre **Exécution**.  
  
## Voir aussi  
 [Fenêtre Exécution](../ide/reference/immediate-window.md)