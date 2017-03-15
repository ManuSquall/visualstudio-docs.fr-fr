---
title: "&lt;erreur&gt;&#160;: &#39;&lt;nom_classe1&gt;&#39; h&#233;rite de &#39;&lt;nom_classe2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;erreur&gt;&#160;: &#39;&lt;nom_classe1&gt;&#39; h&#233;rite de &#39;&lt;nom_classe2&gt;&#39;
Une hiérarchie d’héritage circulaire a été détectée. Une classe est désignée comme héritant d’elle\-même ou d’une autre classe qui hérite directement ou finalement d’elle.  
  
 Ce message peut apparaître plusieurs fois pour suivre le chemin de l’héritage circulaire.  
  
 **ID d’erreur :** BC30256  
  
### Pour corriger cette erreur  
  
-   Brisez la circularité en supprimant au moins une instruction `Inherits` dans le chemin de l’héritage circulaire.  
  
## Voir aussi  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)