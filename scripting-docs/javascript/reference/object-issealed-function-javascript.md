---
title: "Object.isSealed, fonction (JavaScript) | Microsoft Docs"
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
  - "isSealed (fonction) (JavaScript)"
  - "Object.isSealed (JavaScript)"
  - "propriétés (JavaScript), Verrouillage des attributs"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Object.isSealed, fonction (JavaScript)
Retourne la valeur `true` si les attributs de propriété existants ne peuvent pas être modifiés dans un objet et que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.  
  
## Syntaxe  
  
```javascript  
Object.isSealed(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet à tester.  
  
## Valeur de retour  
 `true` si les deux éléments suivants sont true :  
  
-   L'objet est non extensible, ce qui indique que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.  
  
-   L'attribut `configurable` a la valeur `false` pour toutes les propriétés existantes.  
  
 Si l'objet n'a pas de propriété, la fonction retourne la valeur `true` à condition que l'objet soit non extensible.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
 Lorsque l'attribut `configurable` d'une propriété a la valeur `false`, les attributs de propriété ne peuvent pas être modifiés et la propriété ne peut pas être supprimée.  Lorsque l'attribut `writable` a la valeur `false`, la valeur de propriété des données ne peut pas être modifiée.  Lorsque l'attribut `configurable` a la valeur `false` et que l'attribut `writable` a la valeur `true`, les attributs `value` et `writable` peuvent être modifiés.  
  
 La fonction `Object.isSealed` n'utilise pas l'attribut `writable` des propriétés pour déterminer sa valeur de retour.  
  
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
|`Object.isSealed`|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.isSealed`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
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
 [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)