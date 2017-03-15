---
title: "&#39;Sub New&#39; ne peut pas impl&#233;menter des membres d’interface | Microsoft Docs"
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
  - "bc31042"
  - "vbc31042"
helpviewer_keywords: 
  - "BC31042"
ms.assetid: 43ad231f-878d-4d08-b43c-06bf167ddd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; ne peut pas impl&#233;menter des membres d’interface
`Sub New` est un constructeur. Il ne peut pas implémenter de membres.  
  
 **ID d’erreur :** BC31042  
  
### Pour corriger cette erreur  
  
-   Supprimez les instructions `Implements` des procédures `Sub New`.  
  
## Voir aussi  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)