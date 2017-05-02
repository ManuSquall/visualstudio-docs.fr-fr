---
title: "get, m&#233;thode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get, m&#233;thode (WeakMap) (JavaScript)
Retourne un élément spécifié d'un objet `WeakMap`.  
  
## Syntaxe  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### Paramètres  
 `weakmapObj`  
 Requis.  Objet `WeakMap`.  
  
 `key`  
 Requis.  Clé d'un élément dans `WeakMap`.  
  
## Valeur de propriété\/valeur de retour  
 Retourne l'objet associé à la clé.  Si `WeakMap` ne contient pas la clé, cette méthode retourne une valeur `undefined`.  
  
## Exemple  
 L'exemple suivant montre comment récupérer des membres dans un objet `WeakMap`.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]