---
title: "delete, m&#233;thode (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete, m&#233;thode (WeakMap) (JavaScript)
Supprime l'élément spécifié d'un objet `WeakMap`.  
  
## Syntaxe  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### Paramètres  
 `weakmapObj`  
 Requis.  Objet `WeakMap`.  
  
 `key`  
 Requis.  Clé de l'élément à supprimer.  
  
## Valeur de propriété\/valeur de retour  
 `true`si l'élément a été supprimé.  
  
## Exemple  
 L'exemple suivant montre comment ajouter un membre à `WeakMap` puis le supprimer.  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]