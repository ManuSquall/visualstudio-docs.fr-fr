---
title: "&#39;Do&#39; doit se terminer par un &#39;Loop&#39; correspondant | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Do&#39; doit se terminer par un &#39;Loop&#39; correspondant
Une instruction `Do` se produit sans instruction `Loop` correspondante. Vous devez utiliser une instruction `Loop` pour terminer la boucle `Do`.  
  
 **ID d’erreur :** BC30083  
  
### Pour corriger cette erreur  
  
-   Si cette boucle `Do` fait partie d’un ensemble de boucles imbriquées, vérifiez que chaque boucle est correctement terminée.  
  
-   Ajoutez une instruction `Loop` à la fin de la boucle `Do`.  
  
## Voir aussi  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)