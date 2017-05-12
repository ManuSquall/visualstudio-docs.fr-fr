---
title: "Object.getOwnPropertyNames, fonction (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames (méthode) (JavaScript)"
  - "Object.getOwnPropertyNames (méthode) (JavaScript)"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames, fonction (JavaScript)
Retourne les noms des propriétés propres à un objet.  Les propriétés propres à un objet sont celles définies directement sur cet objet ; elles ne sont pas héritées du prototype de l'objet.  Les propriétés d'un objet incluent des champs \(objets\) et des fonctions.  
  
## Syntaxe  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`object`|Obligatoire.  Objet contenant les propriétés propres.|  
  
## Valeur de retour  
 Tableau qui contient les noms des propriétés propres à l'objet.  
  
## Exceptions  
 Si la valeur fournie pour l'argument `object` n'est pas le nom d'un objet, une exception `TypeError` est levée.  
  
## Notes  
 La méthode `getOwnPropertyNames` retourne les noms des propriétés et méthodes énumérables et non énumérables.  Pour retourner uniquement les noms des propriétés et méthodes énumérables, utilisez [Object.keys, fonction](../../javascript/reference/object-keys-function-javascript.md).  
  
## Exemple  
 L'exemple suivant crée un objet comportant trois propriétés et une méthode.  Il utilise ensuite la méthode `getOwnPropertyNames` pour obtenir les propriétés propres à l'objet \(notamment la méthode\).  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## Exemple  
 L'exemple suivant affiche les noms des propriétés commençant par la lettre « s » dans un objet spaghetti construit avec le constructeur Pasta.  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.keys, fonction](../../javascript/reference/object-keys-function-javascript.md)