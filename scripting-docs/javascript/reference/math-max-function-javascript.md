---
title: "Math.max, fonction (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max (méthode)"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max, fonction (JavaScript)
Retourne le plus grand ensemble d'expressions numériques fournies.  
  
## Syntaxe  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## Notes  
 Les arguments facultatifs `number1, number2, ..., numberN` sont des expressions numériques à évaluer.  
  
 Si aucun argument n'est fourni, la valeur de retour est égale à [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Si l'un des arguments correspond à `NaN`, la valeur de retour est également égale à `NaN`.  
  
## Exemple  
 Le code suivant montre comment obtenir la plus grande de deux expressions.  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Math.min, fonction](../../javascript/reference/math-min-function-javascript.md)