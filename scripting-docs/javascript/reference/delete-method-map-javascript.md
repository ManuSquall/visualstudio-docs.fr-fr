---
title: "delete, m&#233;thode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete, m&#233;thode (Map) (JavaScript)
Supprime l'élément spécifié dans un mappage.  
  
## Syntaxe  
  
```javascript  
mapObj.delete(key)  
```  
  
#### Paramètres  
 `mapObj`  
 Requis.  Objet `Map`.  
  
 `key`  
 Requis.  Clé de l'élément à supprimer.  
  
## Valeur de propriété\/valeur de retour  
 `true`si l'élément a été supprimé.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à `Map`, puis supprimer l'un d'eux.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]