---
title: "Math.min, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min (méthode)"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min, fonction (JavaScript)
Retourne le plus petit d'un jeu d'expressions numériques.  
  
## Syntaxe  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## Notes  
 Les arguments facultatifs `number1, number2, ..., numberN` sont des expressions numériques à évaluer.  
  
 Si aucun argument n'est fourni, la valeur de retour est égale à [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Si l'un des arguments correspond à `NaN`, la valeur de retour est également égale à `NaN`.  
  
## Exemple  
 Le code suivant montre comment obtenir la plus petite de deux expressions.  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Math.max, fonction](../../javascript/reference/math-max-function-javascript.md)