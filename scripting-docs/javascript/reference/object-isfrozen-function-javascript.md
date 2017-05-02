---
title: "Object.isFrozen, fonction (JavaScript) | Microsoft Docs"
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
  - "isFrozen (fonction) (JavaScript)"
  - "Object.isFrozen (fonction) (JavaScript)"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isFrozen, fonction (JavaScript)
Retourne la valeur `true` si les attributs et valeurs de propriété existants ne peuvent pas être modifiés dans un objet, et que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.  
  
## Syntaxe  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet à tester.  
  
## Valeur de retour  
 `true` si tous les éléments suivants sont vrais :  
  
-   L'objet est non extensible, ce qui indique que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.  
  
-   L'attribut `configurable` a la valeur `false` pour toutes les propriétés existantes.  
  
-   L'attribut `writable` a la valeur `false` pour toutes les propriétés de données existantes.  
  
 Si l'objet n'a aucune propriété existante, la fonction retourne la valeur `true` si l'objet est non extensible.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
 Lorsque l'attribut `configurable` d'une propriété a la valeur `false`, les attributs de propriété ne peuvent pas être modifiés et la propriété ne peut pas être supprimée.  Lorsque l'attribut `writable` a la valeur `false`, la valeur de propriété des données ne peut pas être modifiée.  Lorsque l'attribut `configurable` a la valeur `false` et que l'attribut `writable` a la valeur `true`, les attributs `value` et `writable` peuvent être modifiés.  
  
 Pour plus d'informations sur la façon de définir des attributs de propriété, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  Pour obtenir les attributs d'une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Fonctions associées  
 Les fonctions associées suivantes empêchent la modification des attributs d'objet.  
  
|Fonction|L'objet est rendu non extensible|`configurable` a la valeur `false` pour chaque propriété|`writable` a la valeur `false` pour chaque propriété|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Les fonctions suivantes retournent la valeur `true` si toutes les conditions indiquées dans le tableau suivant sont remplies.  
  
|Fonction|L'objet est\-il extensible ?|`configurable` a\-t\-il la valeur `false` pour toutes les propriétés ?|`writable` a\-t\-il la valeur `false` pour toutes les propriétés de données ?|  
|--------------|----------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|`Object.isFrozen`|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.isFrozen`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.preventExtensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md)