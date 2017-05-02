---
title: "Number.isFinite, fonction (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isFinite, fonction (Number) (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est un nombre fini.  
  
## Syntaxe  
  
```  
Number.isFinite(numValue)   
```  
  
## Valeur de retour  
 `false` si la valeur est `NaN`, `+∞` ou `-∞` ; sinon `true`.  
  
## Notes  
  
## Exemple  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)