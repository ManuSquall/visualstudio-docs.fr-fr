---
title: "Dans les classes, &#39;Handles&#39; doit sp&#233;cifier une variable &#39;WithEvents&#39;, ou &#39;MyBase&#39;, &#39;MyClass&#39; ou &#39;Me&#39; qualifi&#233; par un identificateur unique | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Dans les classes, &#39;Handles&#39; doit sp&#233;cifier une variable &#39;WithEvents&#39;, ou &#39;MyBase&#39;, &#39;MyClass&#39; ou &#39;Me&#39; qualifi&#233; par un identificateur unique
Pour spécifier un gestionnaire d’événements, les instructions `Handles` doivent spécifier une variable objet déclarée avec le mot clé `WithEvents` ou un membre qualifié avec le mot clé `MyBase`.  
  
 **ID d’erreur :** BC31412  
  
### Pour corriger cette erreur  
  
1.  Utilisez le modificateur `WithEvents` pour déclarer les variables à utiliser avec l’instruction `Handles`.  
  
2.  Spécifiez le nom d’un événement pour la classe active dans la classe de base.  
  
## Voir aussi  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)