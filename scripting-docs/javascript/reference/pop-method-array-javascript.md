---
title: "pop, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop (méthode)"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop, m&#233;thode (Array) (JavaScript)
Supprime le dernier élément d'un tableau et le retourne.  
  
## Syntaxe  
  
```  
  
arrayObj.pop( )  
```  
  
## Notes  
 Les méthodes [push](../../javascript/reference/push-method-array-javascript.md) et `pop` vous permettent de simuler une pile, qui utilise le principe du dernier entré, premier sorti \(LIFO, Last\-In\-First\-Out\) pour stocker les données.  
  
 La référence `arrayObj` requise est un objet `Array`.  
  
 Si le tableau est vide, la valeur `undefined` est retournée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `pop`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [push, méthode \(Array\)](../../javascript/reference/push-method-array-javascript.md)