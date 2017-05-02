---
title: "Math.hypot, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Math.hypot, fonction (JavaScript)
Retourne la racine carrée de la somme des carrés des arguments.  
  
## Syntaxe  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### Paramètres  
 `value1`  
 Obligatoire.  Premier nombre.  
  
 `value2`  
 Facultatif.  Second nombre.  
  
 `values`  
 Facultatif.  Un ou plusieurs nombres.  
  
## Notes  
 Si un argument a la valeur NaN, la fonction retourne NaN.  Si aucun argument n'est fourni, la fonction retourne 0.  
  
## Exemple  
 L'exemple suivant indique comment utiliser la fonction `Math.hypot`.  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]