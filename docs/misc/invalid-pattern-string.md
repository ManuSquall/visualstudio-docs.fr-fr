---
title: "Cha&#238;ne de mod&#232;le non valide | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cha&#238;ne de mod&#232;le non valide
La chaîne de modèle spécifiée dans l’opération `Like` d’une recherche n’est pas valide.  
  
### Pour corriger cette erreur  
  
1.  Examinez les caractères valides des expressions de liste.  
  
2.  Dans la plage de modèles, vérifiez que le caractère de début de plage est inférieur au caractère de fin de plage, comme dans `[a-z]`.  
  
3.  Dans la plage de modèles, vérifiez que plusieurs traits d’union ne se situent pas les uns à côté des autres, comme dans `[a--z]`.  
  
4.  Terminez les plages de modèles par un crochet fermant.  
  
## Voir aussi  
 [Like Operator](/dotnet/visual-basic/language-reference/operators/like-operator)