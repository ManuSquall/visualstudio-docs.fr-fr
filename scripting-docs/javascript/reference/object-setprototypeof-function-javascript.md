---
title: "Object.setPrototypeOf, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Object.setPrototypeOf, fonction (JavaScript)
Définit le prototype d'un objet.  
  
## Syntaxe  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### Paramètres  
 `obj`  
 Obligatoire.  Objet pour lequel vous définissez le prototype.  
  
 `proto`  
 Obligatoire.  Nouvel objet de prototype.  
  
## Notes  
  
> [!WARNING]
>  La définition du prototype peut réduire les performances de tout le code JavaScript qui a accès à un objet dont le prototype a été muté.  
  
## Exemple  
 L'exemple de code suivant montre comment définir le prototype pour un objet.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.getPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter des propriétés à un objet en les ajoutant au prototype.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.getPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Exemple  
 L'exemple de code suivant ajoute des propriétés à l'objet `String` en définissant un nouveau prototype dessus.  
  
```javascript  
var stringProp = { desc: "description" };  
  
Object.getPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.getPrototypeOf(s1, String); // Can't be set.  
    Object.getPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]