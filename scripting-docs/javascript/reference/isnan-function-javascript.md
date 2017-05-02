---
title: "isNaN, fonction (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN (méthode)"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN, fonction (JavaScript)
Retourne une valeur booléenne indiquant si une valeur correspond à la valeur réservée `NaN` \(Not a Number, pas un nombre\).  
  
## Syntaxe  
  
```  
isNaN(numValue)   
```  
  
## Valeur de retour  
 `true` si la valeur convertie en type `Number` est de type `NaN` ; sinon, `false`.  
  
## Notes  
 La valeur `numValue` requise est la valeur à tester par rapport à `NaN`.  
  
 Cette méthode est généralement utilisée pour tester les valeurs de retour des méthodes `parseInt` et `parseFloat`.  
  
 Par ailleurs, une variable contenant `NaN` ou une autre valeur peut être comparée à elle\-même.  Si elle est différente, c'est une valeur `NaN`,  car `NaN` est la seule valeur qui n'est pas égale à elle\-même.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Exemple  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## Voir aussi  
 [Fonction isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN, constante](../../javascript/reference/nan-constant-javascript.md)   
 [Fonction parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Fonction parseInt](../../javascript/reference/parseint-function-javascript.md)