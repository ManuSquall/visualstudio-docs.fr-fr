---
title: "delete, m&#233;thode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete, m&#233;thode (Set) (JavaScript)
Supprime l'élément spécifié dans un ensemble.  
  
## Syntaxe  
  
```javascript  
setObj.delete(value)  
```  
  
#### Paramètres  
 `setObj`  
 Requis.  Objet `Set`.  
  
 `value`  
 Requis.  Élément à supprimer.  
  
## Valeur de propriété\/valeur de retour  
 `true`si l'élément a été supprimé.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à `Set`, puis supprimer l'un d'eux.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]