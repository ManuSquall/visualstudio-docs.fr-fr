---
title: "Instructions et &#233;tiquettes non valides entre &#39;Select Case&#39; et la premi&#232;re occurrence de &#39;Case&#39; | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instructions et &#233;tiquettes non valides entre &#39;Select Case&#39; et la premi&#232;re occurrence de &#39;Case&#39;
Une instruction autre qu’un commentaire se trouve entre l’instruction d’ouverture `Select` ou `Select Case` et sa première instruction `Case`.  
  
 **ID d’erreur :** BC30058  
  
### Pour corriger cette erreur  
  
-   Si l’instruction intermédiaire est un commentaire, précédez\-la d’un délimiteur de commentaire \(`'` ou `REM`\). Sinon, déplacez ou supprimez l’instruction.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)