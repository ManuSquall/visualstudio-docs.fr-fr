---
title: "Collections (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Collections (JavaScript)
Vous pouvez utiliser les objets de collection [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) et [WeakMap](../../javascript/reference/weakmap-object-javascript.md) pour stocker les valeurs et les objets.  Ces objets fournissent des méthodes pratiques pour ajouter et extraire les membres en utilisant une clé ou une valeur au lieu d'un index.  Pour accéder aux membres d'une collection à l'aide d'un index, utilisez un objet `Array`.  Pour plus d'informations, consultez [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set` et `WeakMap` ne sont pas pris en charge dans le navigateur avant Internet Explorer 11.  Pour plus d'informations sur la prise en charge des versions, consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md).  
  
## Utiliser des collections  
 Les objets `Map` et `WeakMap` stockent des paires clé\/valeur et vous permettent d'ajouter, de récupérer et de supprimer des membres à l'aide de la clé.  La clé et la valeur peuvent être de n'importe quel type.  L'objet `Set` stocke les valeurs de n'importe quel type.  
  
 Les objets `Map` et `Set` vous permettent d'énumérer les membres de collection en utilisant la méthode `forEach` et de contrôler la taille de la collection à l'aide de la méthode `size`.  L'objet `WeakMap`, en revanche, n'est pas énumérable.  Pour cette collection, les références principales sont conservées faiblement.  Utilisez `WeakMap` pour que le garbage collector détermine si l'application doit garder chaque membre de la collection en mémoire.  Par exemple, cela peut être utile dans les scénarios de mise en cache où les objets mis en cache sont volumineux et que vous ne souhaitez pas conserver des objets en mémoire inutilement.  Dans certains scénarios, vous pouvez utiliser cet objet pour éviter les fuites de mémoire.  
  
 L'exemple ci\-dessous explique comment utiliser l'objet `Map`.  Dans cet exemple, vous accédez aux membres à l'aide de `get` et de `forEach`.  La fonction de rappel dans `forEach` peut prendre jusqu'à trois paramètres, qui fournissent la valeur de l'élément actuel de la collection, sa clé et l'objet de collection proprement dit.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 L'utilisation de `WeakMap` est semblable à `Map`, excepté que vous ne pouvez extraire les membres qu'à l'aide de `get`.  Pour obtenir un exemple, consultez l'objet [WeakMap](../../javascript/reference/weakmap-object-javascript.md).  
  
 L'exemple ci\-dessous explique comment utiliser l'objet `Set`.  Dans cet exemple, la fonction de rappel prend un paramètre, qui est la valeur de l'élément actuel de collection.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Voir aussi  
 [JavaScript avancé](../../javascript/advanced/advanced-javascript.md)