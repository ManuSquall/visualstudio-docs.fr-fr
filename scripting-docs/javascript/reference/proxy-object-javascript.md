---
title: L’objet proxy (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899595"
---
# <a name="proxy-object-javascript"></a>Objet proxy (JavaScript)
Active le comportement personnalisé d'un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `target`  
 Obligatoire. Objet ou fonction à virtualiser par le proxy.  
  
 `handler`  
 Obligatoire. Objet avec des méthodes (interruptions) qui implémentent le comportement personnalisé.  
  
## <a name="remarks"></a>Notes  
 Un objet `Proxy` est utilisé pour intercepter les opérations internes de bas niveau sur un autre objet. Les objets de proxy peuvent être utilisés pour l'interception, la virtualisation d'objet, la journalisation/le profilage et autres objectifs.  
  
 Si l'interruption d'une opération spécifique n'a pas été définie dans le gestionnaire du proxy, l'opération est transmise à la cible.  
  
 L'objet gestionnaire définit les méthodes suivantes (interruptions) pour implémenter un comportement personnalisé. Les exemples fournis ne sont pas exhaustifs. Pour prendre en charge le comportement par défaut conditionnel dans la méthode de gestionnaire, utilisez les méthodes de [reflètent l’objet](../../javascript/reference/reflect-object-javascript.md).  
  
|Syntaxe de la méthode du gestionnaire (interruptions)|Exemples d'utilisation|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Interruption pour un appel de fonction.|  
|`construct: function(target, args)`|Interruption pour un constructeur.|  
|`defineProperty: function(target, propertyName, descriptor)`|Interruption pour [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Interruption pour l'instruction `delete`.|  
|`enumerate: function(target)`|Interruption pour le [for.. dans](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instruction, [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) (fonction), et [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Interruption pour les [getter](../../javascript/creating-objects-javascript.md) propriétés.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Interruption pour [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Interruption pour [Object.getprototypeof, fonction](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Interruption pour le `in` (opérateur), [hasOwnProperty, méthode (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)et d’autres méthodes.|  
|`isExtensible: function(target)`|Interruption pour [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Interruption pour [Object.getownpropertynames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Interruption pour [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Interruption pour les [setter](../../javascript/creating-objects-javascript.md) propriétés.|  
|`setPrototypeOf: function(target, prototype)`|Interruption pour [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment créer un proxy pour un objet littéral en utilisant l'interruption `get`.  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment créer un proxy pour une fonction en utilisant l'interruption `apply`.  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
