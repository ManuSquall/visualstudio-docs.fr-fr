---
title: "Array.isArray, fonction (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Array.isArray (fonction) (JavaScript)"
  - "isArray (fonction) (JavaScript)"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray, fonction (JavaScript)
Détermine si un objet est un tableau.  
  
## Syntaxe  
  
```  
Array.isArray(object)   
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet à tester.  
  
## Valeur de retour  
 `true` si `object` est un tableau ; sinon, `false`.  Si l'argument `object` n'est pas un objet, `false` est retourné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Array.isArray`.  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof, opérateur](../../javascript/reference/typeof-operator-decrementjavascript.md)