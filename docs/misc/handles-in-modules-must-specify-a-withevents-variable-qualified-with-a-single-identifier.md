---
title: "&#39;Handles&#39; dans les modules doivent sp&#233;cifier une variable &#39;WithEvents&#39; qualifi&#233;e avec un unique identificateur | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; dans les modules doivent sp&#233;cifier une variable &#39;WithEvents&#39; qualifi&#233;e avec un unique identificateur
Pour spécifier un gestionnaire d’événements, les instructions `Handles` doivent spécifier une variable objet ayant été déclarée avec le mot clé `WithEvents`.  
  
 **ID d'erreur :** BC31418  
  
### Pour corriger cette erreur  
  
-   Utilisez le modificateur `WithEvents` pour déclarer des variables qui seront utilisées avec l’instruction `Handles`.  
  
## Voir aussi  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)