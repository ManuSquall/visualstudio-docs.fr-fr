---
title: "La premi&#232;re instruction du corps d’une m&#233;thode ne peut pas se trouver sur la m&#234;me ligne que la d&#233;claration de la m&#233;thode | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La premi&#232;re instruction du corps d’une m&#233;thode ne peut pas se trouver sur la m&#234;me ligne que la d&#233;claration de la m&#233;thode
Une instruction `Function`, `Sub`, `Get`, `Set` ou `Property` doit être seule sur une ligne de code source.  
  
 **ID d’erreur :** BC30040  
  
### Pour corriger cette erreur  
  
1.  Supprimez toute étiquette de ligne précédant la déclaration de procédure.  
  
2.  Déplacez toute instruction précédant la déclaration de procédure vers une ligne de code source antérieure.  
  
3.  Déplacez toute instruction suivant la déclaration de procédure vers une ligne de code source ultérieure.  
  
## Voir aussi  
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)