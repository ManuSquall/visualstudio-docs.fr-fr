---
title: "has, m&#233;thode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has, m&#233;thode (WeakMap) (JavaScript)
Retourne `true` si l'objet `WeakMap` contient l'élément spécifié.  
  
## Syntaxe  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### Paramètres  
 `weakmapObj`  
 Requis.  Objet `WeakMap`.  
  
 `key`  
 Requis.  Clé de l'élément à tester.  
  
## Valeur de propriété\/valeur de retour  
 `true` si le `WeakMap` contient la clé spécifiée.  
  
## Exemple  
 L'exemple suivant montre comment ajouter un membre à `WeakMap`, puis utiliser `has` pour vérifier s'il est présent.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]