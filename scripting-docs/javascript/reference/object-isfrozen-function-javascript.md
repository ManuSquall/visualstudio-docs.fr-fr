---
title: Object.IsFrozen, fonction (JavaScript) | Documents Microsoft
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
helpviewer_keywords:
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641709"
---
# <a name="objectisfrozen-function-javascript"></a>Object.isFrozen, fonction (JavaScript)
Retourne `true` si les attributs de propriété et les valeurs existantes ne peut pas être modifiés dans un objet, et nouvelles propriétés ne peuvent pas être ajoutées à l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si toutes les conditions suivantes sont remplies :  
  
-   L’objet est non extensible, ce qui signifie que les nouvelles propriétés ne peuvent pas être ajoutées à l’objet.  
  
-   Le `configurable` attribut est `false` pour toutes les propriétés existantes.  
  
-   Le `writable` attribut est `false` pour toutes les propriétés de données existantes.  
  
 Si l’objet n’a pas de propriétés existantes, la fonction retourne `true` si l’objet est non extensible.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le `configurable` d’une propriété de l’attribut est `false`, les attributs de propriété ne peut pas être modifiés et que la propriété ne peut pas être supprimée. Lorsque `writable` est `false`, la valeur de propriété de données ne peut pas être modifiée. Lorsque `configurable` est `false` et `writable` est `true`, le `value` et `writable` attributs peuvent être modifiés.  
  
 Pour plus d’informations sur la façon de définir les attributs de propriété, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md). Pour obtenir les attributs d’une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Les fonctions associées suivantes empêchent la modification des attributs d’objet.  
  
|Fonction|Objet devient non extensible|`configurable`a la valeur `false` pour chaque propriété.|`writable`a la valeur `false` pour chaque propriété.|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Ces fonctions retournent `true` si toutes les conditions sont marqués dans le tableau suivant sont remplies.  
  
|Fonction|Objet est extensible ?|`configurable`est `false` pour toutes les propriétés ?|`writable`est `false` pour toutes les propriétés de données ?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|`Object.isFrozen`|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.isFrozen`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.IsSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Fonction Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)