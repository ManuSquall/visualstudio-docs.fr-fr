---
title: "Object.isExtensible, fonction (JavaScript) | Microsoft Docs"
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
  - "isExtensible (fonction) (JavaScript)"
  - "Object.isExtensible (fonction) (JavaScript)"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isExtensible, fonction (JavaScript)
Retourne une valeur qui indique si de nouvelles propriétés peuvent être ajoutées à un objet.  
  
## Syntaxe  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet à tester.  
  
## Valeur de retour  
 La valeur est `true` si l'objet est extensible, ce qui indique que de nouvelles propriétés peuvent être ajoutées à l'objet ; sinon, la valeur est `false`.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
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
|`Object.isExtensible`|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.isExtensible`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.preventExtensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)