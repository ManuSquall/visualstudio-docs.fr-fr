---
title: "Number.isInteger, fonction (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isInteger, fonction (Number) (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est un entier.  
  
## Syntaxe  
  
```  
Number.isInteger(numValue)   
```  
  
## Valeur de retour  
 `true` si la valeur est un entier, sinon `false`.  
  
## Notes  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Exemple  
  
```javascript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```