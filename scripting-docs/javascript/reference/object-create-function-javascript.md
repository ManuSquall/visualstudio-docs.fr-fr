---
title: "Object.create, fonction (JavaScript) | Microsoft Docs"
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
  - "create (fonction) (JavaScript)"
  - "Object.create (fonction) (JavaScript)"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create, fonction (JavaScript)
Crée un objet qui a le prototype spécifié et qui contient éventuellement les propriétés spécifiées.  
  
## Syntaxe  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### Paramètres  
 `prototype`  
 Requis.  Objet à utiliser comme prototype.  Il peut avoir la valeur `null`.  
  
 `descriptors`  
 Optionnel.  Un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet qui contient un ou plusieurs descripteurs de propriété.  
  
 Une *propriété de données* est une propriété qui peut obtenir et définir une valeur.  Un descripteur de propriété de données contient un attribut `value`, ainsi que des attributs `writable`, `enumerable` et `configurable`.  Si les trois derniers attributs ne sont pas spécifiés, leur valeur par défaut est `false`.  Une *propriété Accessor* appelle une fonction fournie par l'utilisateur chaque fois que la valeur est récupérée ou définie.  Un descripteur de propriété Accessor contient un attribut `set`, un attribut `get` ou les deux.  Pour plus d'informations, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Valeur de retour  
 Objet qui a le prototype interne spécifié et contient les propriétés spécifiées, le cas échéant.  
  
## Exceptions  
 Une exception `TypeError` est levée si l'une des conditions suivantes a la valeur true :  
  
-   L'argument `prototype` n'est pas un objet et n'a pas la valeur `null`.  
  
-   Un descripteur dans l'argument `descriptors` a un attribut `value` ou `writable` et un attribut `get` ou `set`.  
  
-   Un descripteur dans l'argument `descriptors` a un attribut `get` ou `set` qui n'est pas une fonction.  
  
## Notes  
 Vous pouvez utiliser cette fonction avec un paramètre `null` `prototype` pour arrêter la chaîne prototype.  L'objet créé n'aura aucun prototype.  
  
## Exemple  
 L'exemple suivant crée un objet à l'aide d'un prototype `null` et ajoute deux propriétés énumérables.  
  
```javascript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## Exemple  
 L'exemple suivant crée un objet qui a le même prototype interne que l'objet Object.  Vous pouvez voir qu'il a le même prototype qu'un objet créé à l'aide d'un littéral d'objet.  La fonction [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) obtient le prototype de l'objet d'origine.  Pour obtenir le descripteur de propriété de l'objet, utilisez [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```javascript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## Exemple  
 L'exemple suivant crée un objet qui a le même prototype interne que l'objet Shape.  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.getPrototypeOf, fonction](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf, méthode \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Création d'objets](../../javascript/creating-objects-javascript.md)