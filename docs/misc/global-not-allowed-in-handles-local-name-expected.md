---
title: "&#39;Global&#39; interdit dans les handles&#160;; nom local attendu | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; interdit dans les handles&#160;; nom local attendu
Une clause `Handles` doit faire référence à un événement local. Le mot clé `Global` fournit l’accès aux éléments de programmation globaux.  
  
 **ID d’erreur :** BC36002  
  
### Pour corriger cette erreur  
  
-   Modifiez la clause `Handles` pour faire référence à une instance locale de l’événement au lieu de l’instance globale.  
  
## Voir aussi  
 [Global \- supprimer](http://msdn.microsoft.com/fr-fr/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)