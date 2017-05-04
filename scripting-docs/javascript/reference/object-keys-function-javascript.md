---
title: "Object.keys, fonction (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "keys (méthode) (JavaScript)"
  - "Object.keys (méthode) (JavaScript)"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys, fonction (JavaScript)
Retourne les noms des propriétés et méthodes énumérables d'un objet.  
  
## Syntaxe  
  
```javascript  
Object.keys(object)  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`object`|Obligatoire.  Objet contenant les propriétés et les méthodes.  Il peut s'agir d'un objet que vous avez créé ou d'un objet DOM \(Document Object Model\) existant.|  
  
## Valeur de retour  
 Tableau contenant les noms des propriétés énumérables et des méthodes de l'objet.  
  
## Exceptions  
 Si la valeur fournie pour l'argument `object` n'est pas le nom d'un objet, une exception `TypeError` est levée.  
  
## Notes  
 La méthode `keys` retourne uniquement les noms des propriétés énumérables et des méthodes.  Pour retourner les noms des propriétés énumérables et non énumérables, utilisez la méthode [Object.getOwnPropertyNames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Pour plus d'informations relatives à l'attribut `enumerable` d'une propriété, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md) et [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Exemple  
 L'exemple suivant crée un objet comportant trois propriétés et une méthode.  La méthode `keys` est utilisée ensuite afin d'obtenir les propriétés et les méthodes de l'objet.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## Exemple  
 L'exemple suivant affiche les noms de toutes les propriétés énumérables qui commencent par la lettre « g » dans l'objet Pasta.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.getOwnPropertyNames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md)