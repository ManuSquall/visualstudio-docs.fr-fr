---
title: "Math.imul, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.imul, fonction (JavaScript)
Retourne le produit de deux nombres traités comme des entiers signés 32 bits.  
  
## Syntaxe  
  
```  
Math.imul(x, y);  
```  
  
#### Paramètres  
 `x`  
 Obligatoire.  Premier nombre.  
  
 `y`  
 Obligatoire.  Second nombre.  
  
## Notes  
 Cette fonction est utilisée pour les compilateurs comme Emscripten et Mandreel, qui n'implémentent pas la multiplication d'entiers de la même manière que JavaScript.  
  
## Exemple  
 L'exemple de code suivant montre comment multiplier des nombres avec `Math.imul`.  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]