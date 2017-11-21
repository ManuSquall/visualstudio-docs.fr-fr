---
title: Reflect, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="reflect-object-javascript"></a>Reflect, objet (JavaScript)
Fournit des méthodes à utiliser dans des opérations qui sont interceptées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `method`  
 Requis. Nom de l'une des méthodes de l'objet `Reflect`.  
  
## <a name="remarks"></a>Remarques  
 L'objet Reflect ne peut pas être instancié avec l'opérateur `new`.  
  
 Reflète les méthodes sont souvent utilisées avec [proxys](../../javascript/reference/proxy-object-javascript.md) , car ils permettent de déléguer au comportement par défaut sans avoir à implémenter le comportement par défaut dans votre code.  
  
 Reflect fournit une méthode statique avec le même nom que chaque interruption du proxy. Les descriptions dans le tableau ne sont pas exhaustives.  
  
|Méthode|Description|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Similaire à la [appliquer](../../javascript/reference/apply-method-function-javascript.md) méthode de l’objet de fonction.|  
|`Reflect.construct(target, args)`|Équivalent de fonction pour l'opérateur `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Semblable à [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.deleteProperty(target, propertyName)`|Semblable à l'instruction `delete`. Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.enumerate(target)`|Semblable à [for.. dans](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instruction, [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) (fonction), et [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Une fonction équivalente d’any [getter](../../javascript/creating-objects-javascript.md) propriétés.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Semblable à [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.getPrototypeOf(target)`|Semblable à [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Similaire à la `in` (opérateur), [hasOwnProperty, méthode (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)et d’autres méthodes. Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.isExtensible(target)`|Semblable à [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Semblable à [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Semblable à [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md). Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.set(target, propertyName, value, receiver)`|Similaire à celle d’un [setter](../../javascript/creating-objects-javascript.md) propriété. Retourne une valeur booléenne indiquant si l'appel a réussi.|  
|`Reflect.setPrototypeOf(target, prototype)`|Semblable à [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md). Retourne une valeur booléenne indiquant si l'appel a réussi.|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment utiliser `Reflect.get` pour écrire un proxy qui bloque les opérations get pour les propriétés qui commencent par un trait de soulignement.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]