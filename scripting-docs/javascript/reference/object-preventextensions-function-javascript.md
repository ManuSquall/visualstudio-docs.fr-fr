---
title: "Object.preventExtensions, fonction (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions (fonction) (JavaScript)"
  - "preventExtensions (fonction) (JavaScript)"
  - "éviter les nouvelles propriétés (JavaScript)"
  - "propriétés (JavaScript), éviter la création de"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions, fonction (JavaScript)
Empêche l'ajout de nouvelles propriétés à un objet.  
  
## Syntaxe  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet à rendre non extensible.  
  
## Valeur de retour  
 Objet passé à la fonction.  
  
## Exceptions  
 Si l'argument n'est pas un objet `object`, une exception `TypeError` est levée.  
  
## Notes  
 La fonction `Object.preventExtensions` rend un objet non extensible, afin que les nouvelles propriétés nommées ne puissent pas être ajoutées à celui\-ci.  Une fois qu'un objet a été rendu non extensible, il ne peut plus être rendu de nouveau extensible.  
  
 Pour plus d'informations sur la façon de définir des attributs de propriété, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Fonctions associées  
 Les fonctions associées suivantes empêchent la modification des attributs d'objet.  
  
|Fonction|L'objet est rendu non extensible|`configurable` a la valeur `false` pour chaque propriété|`writable` a la valeur `false` pour chaque propriété|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|`Object.preventExtensions`|Oui|Non|Non|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Les fonctions suivantes retournent la valeur `true` si toutes les conditions indiquées dans le tableau suivant sont remplies.  
  
|Fonction|L'objet est\-il extensible ?|`configurable` a\-t\-il la valeur `false` pour toutes les propriétés ?|`writable` a\-t\-il la valeur `false` pour toutes les propriétés de données ?|  
|--------------|----------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Object.preventExtensions`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)