---
title: "set, m&#233;thode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set, m&#233;thode (WeakMap) (JavaScript)
Ajoute un nouvel élément à un objet `WeakMap`.  
  
## Syntaxe  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### Paramètres  
 `weakmapObj`  
 Requis.  Objet `WeakMap`.  
  
 `key`  
 Requis.  Objet représentant la clé de l'élément à ajouter.  Ce doit être une référence d'objet .  
  
 `value`  
 Requis.  Valeur de l'élément à ajouter.  
  
## Valeur de propriété\/valeur de retour  
 Retourne l'objet `WeakMap` qui contient la nouvelle paire clé\/valeur.  
  
## Notes  
 Si vous ajoutez une valeur à la collection à l'aide d'une clé existante, la nouvelle valeur remplace l'ancienne valeur.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un objet `WeakMap`.  
  
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
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]