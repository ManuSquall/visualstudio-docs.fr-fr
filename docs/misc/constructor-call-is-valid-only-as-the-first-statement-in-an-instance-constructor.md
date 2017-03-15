---
title: "Un appel de constructeur est valide uniquement en tant que premi&#232;re instruction dans un constructeur d’instance | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un appel de constructeur est valide uniquement en tant que premi&#232;re instruction dans un constructeur d’instance
Un appel à `New()` se produit après la première instruction d’un constructeur. Si un constructeur en appelle un autre explicitement, il doit le faire dans la première instruction qui suit l’instruction `Sub New()`.  
  
 **ID d’erreur :** BC30282  
  
### Pour corriger cette erreur  
  
-   Supprimez l’appel à `New()`, ou déplacez\-le au début du constructeur.  
  
## Voir aussi  
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)