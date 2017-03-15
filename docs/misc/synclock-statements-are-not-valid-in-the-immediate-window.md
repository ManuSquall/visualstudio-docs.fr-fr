---
title: "Les instructions &#39;SyncLock&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution | Microsoft Docs"
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
  - "vbc30135"
  - "bc30135"
helpviewer_keywords: 
  - "BC30135"
ms.assetid: 099771a1-5bf4-4c16-8fc3-262926c771df
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;SyncLock&#39; ne sont pas valides dans la fen&#234;tre Ex&#233;cution
L’instruction `SyncLock` synchronise les threads et n’est pas autorisée dans un contexte de débogage.  
  
 **ID d’erreur :** BC30135  
  
### Pour corriger cette erreur  
  
-   N’émettez pas une instruction `SyncLock` dans la fenêtre **Exécution**.  
  
## Voir aussi  
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)