---
title: "add, m&#233;thode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# add, m&#233;thode (WeakSet) (JavaScript)
Ajoute un nouvel élément à `WeakSet`.  
  
## Syntaxe  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### Paramètres  
 `weaksetObj`  
 Obligatoire.  Objet `WeakSet`.  
  
 `obj`  
 Obligatoire.  Nouvel élément de `WeakSet`.  
  
## Notes  
 Le nouvel élément doit être un objet, plutôt qu'une valeur arbitraire, et doit être unique.  Si vous ajoutez un élément non unique à un `WeakSet`, le nouvel élément ne sera pas ajouté à la collection.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un ensemble, puis vérifier qu'ils ont été ajoutés.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]