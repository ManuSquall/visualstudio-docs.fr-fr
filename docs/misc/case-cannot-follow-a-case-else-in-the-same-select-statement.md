---
title: "&#39;Case&#39; ne peut pas suivre &#39;Case Else&#39; dans la m&#234;me instruction &#39;Select&#39; | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; ne peut pas suivre &#39;Case Else&#39; dans la m&#234;me instruction &#39;Select&#39;
Une instruction `Case Else` introduit des instructions à exécuter si aucune correspondance n’est trouvée pour l’instruction `Case` initiale. Une instruction `Case` a été rencontrée après `Case Else` dans le même bloc `Select`.  
  
 **ID d’erreur :** BC30321  
  
### Pour corriger cette erreur  
  
-   Déplacez `Case Else` vers l’emplacement approprié après l’instruction `Case`.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)