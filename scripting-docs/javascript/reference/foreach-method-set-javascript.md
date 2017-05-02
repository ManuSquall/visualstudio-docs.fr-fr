---
title: "forEach, m&#233;thode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach, m&#233;thode (Set) (JavaScript)
Exécute l'action spécifiée pour chaque élément d'un ensemble.  
  
## Syntaxe  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### Paramètres  
 `setObj`  
 Requis.  Objet `Set`.  
  
 `callbackfn`  
 Requis.  `callbackfn` accepte jusqu'à trois arguments.  Fonction que `forEach` appelle une fois pour chaque élément de l'ensemble.  
  
 `thisArg`  
 Optionnel.  Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`.  Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.  
  
## Exceptions  
 Si l'argument `callbackfn`, n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## Notes  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, key, setObj)`  
  
 Vous pouvez déclarer la fonction de rappel en utilisant jusqu'à trois paramètres, comme indiqué dans le tableau suivant.  
  
|Argument de rappel|Définition|  
|------------------------|----------------|  
|`value`|Une valeur contenue dans le jeu.|  
|`key`|Une valeur contenue dans le jeu.  Un ensemble ne comporte aucune clé, donc cette valeur est la même que `value`.|  
|`setObj`|L'objet `Set` à franchir.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser `forEach`.  L'argument `callbackfn` inclut le code de la fonction de rappel.  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## Exemple  
 L'exemple suivant montre que vous pouvez également récupérer des membres d'un ensemble en passant un seul paramètre à la fonction de rappel.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]