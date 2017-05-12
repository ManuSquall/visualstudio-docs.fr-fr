---
title: "set, m&#233;thode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set, m&#233;thode (Map) (JavaScript)
Ajoute un élément à un mappage.  
  
## Syntaxe  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### Paramètres  
 `mapObj`  
 Requis.  Objet `Map`.  
  
 `key`  
 Requis.  Clé du nouvel élément.  
  
 `value`  
 Requis.  Valeur de l'élément à ajouter.  
  
## Valeur de propriété\/valeur de retour  
 Retourne l'objet `Map` qui contient la nouvelle paire clé\/valeur.  
  
## Notes  
 Si vous ajoutez une valeur à la collection à l'aide d'une clé existante, la nouvelle valeur remplace l'ancienne valeur.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à `Map`, puis les extraire.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]