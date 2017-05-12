---
title: "add, m&#233;thode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add, m&#233;thode (Set) (JavaScript)
Ajoute un élément à un ensemble.  
  
## Syntaxe  
  
```javascript  
setObj.add(value)  
```  
  
#### Paramètres  
 `setObj`  
 Requis.  Objet `Set`.  
  
 `value`  
 Requis.  Nouvel élément de `Set`.  
  
## Notes  
 Le nouvel élément peut être de n'importe quel type et doit être unique.  Si vous ajoutez un élément non unique à un `Set`, le nouvel élément ne sera pas ajouté à la collection.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un ensemble, puis les extraire.  
  
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