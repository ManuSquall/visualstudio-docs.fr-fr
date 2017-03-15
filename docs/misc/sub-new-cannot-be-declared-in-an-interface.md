---
title: "&#39;Sub New&#39; ne peut pas &#234;tre d&#233;clar&#233; dans une interface | Microsoft Docs"
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
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; ne peut pas &#234;tre d&#233;clar&#233; dans une interface
Vous avez essayé de déclarer `Sub New` dans une interface. Étant donné qu’il s’agit d’un constructeur, `Sub New` ne peut s’exécuter qu’une seule fois quand une classe est créée. Il ne peut pas être appelé explicitement depuis un autre emplacement que la première ligne de code d’un autre constructeur de la même classe ou d’une classe dérivée.  
  
 **ID d’erreur :** BC30363  
  
### Pour corriger cette erreur  
  
-   Supprimez `Sub New` ou déplacez\-le vers un emplacement plus approprié dans votre code.  
  
## Voir aussi  
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)