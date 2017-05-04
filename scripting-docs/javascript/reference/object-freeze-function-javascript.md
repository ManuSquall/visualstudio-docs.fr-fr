---
title: "Object.freeze, fonction (JavaScript) | Microsoft Docs"
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
  - "freeze (fonction)"
  - "Object.freeze (fonction)"
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Object.freeze, fonction (JavaScript)
Empêche la modification des attributs et valeurs de propriété existants, et empêche l'ajout de nouvelles propriétés.  
  
## Syntaxe  
  
```javascript  
Object.freeze(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet sur lequel verrouiller les attributs.  
  
## Valeur de retour  
 Objet passé à la fonction.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
 La fonction `Object.freeze` effectue les opérations suivantes :  
  
-   Elle rend l'objet non extensible, afin que de nouvelles propriétés ne puissent pas être ajoutées à celui\-ci.  
  
-   Elle affecte à l'attribut `configurable` la valeur `false` pour toutes les propriétés de l'objet.  Lorsque l'attribut `configurable` a la valeur `false`, les attributs de propriété ne peuvent pas être modifiés et la propriété ne peut pas être supprimée.  
  
-   Elle affecte à l'attribut `writable` la valeur `false` pour toutes les propriétés de données de l'objet.  Lorsque l'attribut `writable` a la valeur false, la valeur de la propriété des données ne peut pas être modifiée.  
  
 Pour plus d'informations sur la façon de définir des attributs de propriété, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  Pour obtenir les attributs d'une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Fonctions associées  
 Les fonctions associées suivantes empêchent la modification des attributs d'objet.  
  
|Fonction|L'objet est rendu non extensible|`configurable` a la valeur `false` pour chaque propriété|`writable` a la valeur `false` pour chaque propriété|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|`Object.freeze`|Oui|Oui|Oui|  
  
 Les fonctions suivantes retournent la valeur `true` si toutes les conditions indiquées dans le tableau suivant sont remplies.  
  
|Fonction|L'objet est\-il extensible ?|`configurable` a\-t\-il la valeur `false` pour toutes les propriétés ?|`writable` a\-t\-il la valeur `false` pour toutes les propriétés de données ?|  
|--------------|----------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Oui|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.freeze`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.preventExtensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)