---
title: "forEach, m&#233;thode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# forEach, m&#233;thode (Map) (JavaScript)
Exécute l'action spécifiée pour chaque élément du mappage.  
  
## Syntaxe  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### Paramètres  
 `mapObj`  
 Requis.  Objet `Map`.  
  
 `callbackfn`  
 Requis.  Fonction que `forEach` appelle une fois pour chaque élément du mappage.  `callbackfn` accepte jusqu'à trois arguments.  La méthode `forEach` appelle la fonction `callbackfn` une fois pour chaque élément du mappage.  
  
 `thisArg`  
 Optionnel.  Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`.  Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.  
  
## Exceptions  
 Si l'argument `callbackfn`, n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## Notes  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, key, mapObj)`  
  
 Vous pouvez déclarer la fonction de rappel en utilisant jusqu'à trois paramètres, comme indiqué dans le tableau suivant.  
  
|Argument de rappel|Définition|  
|------------------------|----------------|  
|`value`|Une valeur contenue dans le mappage.|  
|`key`|Une clé contenue dans le mappage.|  
|`mapObj`|L'objet `Map` à franchir.|  
  
## Exemple  
 L'exemple suivant montre comment récupérer les membres de `Map` en utilisant `forEach`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]