---
title: "Impossible de d&#233;finir la valeur d’une variable locale pour une m&#233;thode qui ne se trouve pas au sommet de la pile. | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;finir la valeur d’une variable locale pour une m&#233;thode qui ne se trouve pas au sommet de la pile.
Vous pouvez modifier des variables uniquement si elles figurent en haut de la pile des appels. Par exemple, si `procedure1` appelle `procedure2` et que vous êtes dans `procedure1`, vous ne pouvez pas modifier les variables dans `procedure2`.  
  
 **ID d’erreur :** BC30711  
  
### Pour corriger cette erreur  
  
-   Modifiez les variables qui figurent en haut de la pile des appels.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)