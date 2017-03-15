---
title: "L’h&#233;ritage de &#39;System.&lt;nom_classe&gt;&#39; n’est pas valide | Microsoft Docs"
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
  - "vbc30015"
  - "bc30015"
helpviewer_keywords: 
  - "BC30015"
ms.assetid: b4c005df-a510-47c7-b5cc-27f4514d32b6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’h&#233;ritage de &#39;System.&lt;nom_classe&gt;&#39; n’est pas valide
Une classe ne peut pas hériter de `System.Array`, `System.Delegate`, `System.Enum` ou `System.ValueType`.  
  
 **ID d’erreur :** BC30015  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `Inherits` ou modifiez\-la pour qu’elle hérite d’une classe de base valide.  
  
## Voir aussi  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Object Variable Declaration](/dotnet/visual-basic/programming-guide/language-features/variables/object-variable-declaration)