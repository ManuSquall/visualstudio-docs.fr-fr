---
title: "Reflect, objet (JavaScript) | Microsoft Docs"
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Reflect, objet (JavaScript)
Fournit des méthodes à utiliser dans des opérations qui sont interceptées.  
  
## Syntaxe  
  
```  
Reflect.[method]  
```  
  
#### Paramètres  
 `method`  
 Obligatoire.  Nom de l'une des méthodes de l'objet `Reflect`.  
  
## Notes  
 L'objet Reflect ne peut pas être instancié avec l'opérateur `new`.  
  
 Les méthodes Reflect sont souvent utilisées avec des [serveurs proxy](../../javascript/reference/proxy-object-javascript.md), car elles vous permettent de déléguer au comportement par défaut sans avoir à implémenter le comportement par défaut dans votre code.  
  
 Reflect fournit une méthode statique avec le même nom que chaque interruption du proxy.  Les descriptions dans le tableau ne sont pas exhaustives.  
  
|Méthode|Description|  
|-------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Semblable à la méthode [apply](../../javascript/reference/apply-method-function-javascript.md) de l'objet Function.|  
|`Reflect.construct(target, args)`|Équivalent de fonction pour l'opérateur `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Semblable à [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.deleteProperty(target, propertyName)`|Semblable à l'instruction `delete`.  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.enumerate(target)`|Semblable à l'instruction [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), la fonction [Object.keys](../../javascript/reference/object-keys-function-javascript.md) et [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Équivalent de fonction pour toutes les propriétés [getter](../../javascript/creating-objects-javascript.md).|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Semblable à [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.getPrototypeOf(target)`|Semblable à [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Semblable à l'opérateur `in`, [hasOwnProperty, méthode \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) et d'autres méthodes.  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.isExtensible(target)`|Semblable à [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Semblable à [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Semblable à [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.set(target, propertyName, value, receiver)`|Semblable à l'utilisation d'une propriété [setter](../../javascript/creating-objects-javascript.md).  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.setPrototypeOf(target, prototype)`|Semblable à [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).  Retourne une valeur booléenne indiquant si l'appel a réussi.|  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser `Reflect.get` pour écrire un proxy qui bloque les opérations get pour les propriétés qui commencent par un trait de soulignement.  
  
```javascript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]