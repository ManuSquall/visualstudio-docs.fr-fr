---
title: "Object.seal, fonction (JavaScript) | Microsoft Docs"
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
  - "Object.seal (fonction)"
  - "seal (fonction)"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.seal, fonction (JavaScript)
Empêche la modification des attributs de propriété existants, et empêche l'ajout de nouvelles propriétés.  
  
## Syntaxe  
  
```javascript  
Object.seal(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet sur lequel verrouiller les attributs.  
  
## Valeur de retour  
 Objet passé à la fonction.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
 La fonction `Object.seal` permet d'effectuer ce qui suit :  
  
-   Elle rend l'objet non extensible, afin que de nouvelles propriétés ne puissent pas être ajoutées à celui\-ci.  
  
-   Elle affecte à l'attribut `configurable` la valeur `false` pour toutes les propriétés de l'objet.  
  
 Lorsque l'attribut `configurable` a la valeur `false`, les attributs de propriété ne peuvent pas être modifiés et la propriété ne peut pas être supprimée.  Lorsque l'attribut `configurable` a la valeur `false` et que l'attribut `writable` a la valeur `true`, les attributs `value` et `writable` peuvent être modifiés.  
  
 La fonction `Object.seal` ne modifie pas l'attribut `writable`.  
  
 Pour plus d'informations sur la façon de définir des attributs de propriété, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  Pour obtenir les attributs d'une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Fonctions associées  
 Les fonctions associées suivantes empêchent la modification des attributs d'objet.  
  
|Fonction|L'objet est rendu non extensible|`configurable` a la valeur `false` pour chaque propriété|`writable` a la valeur `false` pour chaque propriété|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|`Object.seal`|Oui|Oui|Non|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Les fonctions suivantes retournent la valeur `true` si toutes les conditions indiquées dans le tableau suivant sont remplies.  
  
|Fonction|L'objet est\-il extensible ?|`configurable` a\-t\-il la valeur `false` pour toutes les propriétés ?|`writable` a\-t\-il la valeur `false` pour toutes les propriétés de données ?|  
|--------------|----------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.seal`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.preventExtensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)