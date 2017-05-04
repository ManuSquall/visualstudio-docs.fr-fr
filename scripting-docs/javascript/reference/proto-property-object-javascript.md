---
title: "__proto__, propri&#233;t&#233; (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__, propri&#233;t&#233; (Object) (JavaScript)
Contient une référence au prototype interne de l'objet spécifié.  
  
## Syntaxe  
  
```  
object.__proto__  
```  
  
#### Paramètres  
 `object`  
 Requis.  Objet dans lequel définir le prototype.  
  
## Notes  
 La propriété `__proto__` peut être utilisée pour définir le prototype pour un objet.  
  
 L'objet ou la fonction hérite de toutes les méthodes et propriétés du nouveau prototype, ainsi que toutes les propriétés et méthodes de la chaîne de prototype du nouveau prototype.  Un objet ne peut avoir qu'un prototype unique \(hormis les prototypes hérités dans la chaîne prototype\), donc lorsque vous appelez la propriété `__proto__`, vous remplacez le prototype précédent.  
  
 Vous ne pouvez définir le prototype que sur un objet extensible.  Pour plus d'informations, consultez [Object.preventExtensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Le nom de propriété `__proto__` commence et se termine par deux traits de soulignement.  
  
## Exemple  
 L'exemple de code suivant montre comment définir la propriété d'un objet .  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## Exemple  
 L'exemple de code suivant indique comment ajouter des propriétés à un objet en les ajoutant au prototype.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Exemple  
 L'exemple de code suivant ajoute des propriétés à l'objet `String` en y définissant un nouveau prototype.  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Prototypes et héritage de prototypes](../../javascript/advanced/prototypes-and-prototype-inheritance.md)