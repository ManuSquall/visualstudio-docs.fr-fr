---
title: "unshift, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift (méthode)"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift, m&#233;thode (Array) (JavaScript)
Insère de nouveaux éléments au début d'un tableau.  
  
## Syntaxe  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Objet `Array`.  
  
 `item1, item2,. . ., itemN`  
 Facultatif.  Éléments à insérer au début de l'objet `Array`.  
  
## Notes  
 La méthode `unshift` insère les éléments au début du tableau, dans l'ordre dans lequel ils s'affichent dans la liste des arguments.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `unshift`.  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [shift, méthode \(Array\)](../../javascript/reference/shift-method-array-javascript.md)