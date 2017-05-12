---
title: "has, m&#233;thode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# has, m&#233;thode (WeakSet) (JavaScript)
Retourne `true` si `WeakSet` contient l'élément spécifié.  
  
## Syntaxe  
  
```javascript  
setObj.has(obj)  
```  
  
#### Paramètres  
 `setObj`  
 Obligatoire.  Objet `WeakSet`.  
  
 `obj`  
 Obligatoire.  Élément à tester.  
  
## Valeur de propriété\/valeur de retour  
 `true` si le jeu contient l'élément spécifié.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un `WeakSet`, puis vérifier si le jeu contient un membre spécifique.  
  
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