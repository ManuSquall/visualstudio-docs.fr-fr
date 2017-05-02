---
title: "delete, m&#233;thode (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# delete, m&#233;thode (WeakSet) (JavaScript)
Supprime l'élément spécifié d'un `WeakSet`.  
  
## Syntaxe  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### Paramètres  
 `weaksetObj`  
 Obligatoire.  Objet `WeakSet`.  
  
 `obj`  
 Obligatoire.  Élément à supprimer.  
  
## Valeur de propriété\/valeur de retour  
 `true` si l'élément a été supprimé.  
  
## Exemple  
 L'exemple suivant montre comment ajouter et supprimer les éléments d'un `WeakSet`.  
  
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