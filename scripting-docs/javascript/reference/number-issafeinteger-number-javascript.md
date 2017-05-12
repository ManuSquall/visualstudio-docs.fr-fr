---
title: "Number.isSafeInteger (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (Number) (JavaScript)
Retourne une valeur booléenne qui indique si un nombre peut être représenté en toute sécurité en JavaScript.  
  
## Syntaxe  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## Valeur de retour  
 `true` si le nombre est compris entre `Number.MIN_SAFE_INTEGER` et `Number.MAX_SAFE_INTEGER` \(inclus\) ; sinon `false`.  
  
## Notes  
 Un entier sûr en JavaScript est un nombre double précision IEEE\-754 avant l'application d'un arrondi.  
  
## Exemple  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)