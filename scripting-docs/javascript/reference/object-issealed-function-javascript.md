---
title: Object.IsSealed, fonction (JavaScript) | Documents Microsoft
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
helpviewer_keywords:
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectissealed-function-javascript"></a>Object.isSealed, fonction (JavaScript)
Retourne la valeur `true` si les attributs de propriété existants ne peuvent pas être modifiés dans un objet et que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si les deux des options suivantes sont vraies :  
  
-   L’objet est non extensible, ce qui signifie que les nouvelles propriétés ne peuvent pas être ajoutées à l’objet.  
  
-   Le `configurable` attribut est `false` pour toutes les propriétés existantes.  
  
 Si l’objet n’a pas de toutes les propriétés, la fonction retourne `true` si l’objet est non extensible.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le `configurable` d’une propriété de l’attribut est `false`, les attributs de propriété ne peut pas être modifiés et que la propriété ne peut pas être supprimée. Lorsque `writable` est `false`, la valeur de propriété de données ne peut pas être modifiée. Lorsque `configurable` est `false` et `writable` est `true`, le `value` et `writable` attributs peuvent être modifiés.  
  
 Le `Object.isSealed` fonction n’utilise pas le `writable` attribut des propriétés pour déterminer sa valeur de retour.  
  
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
|`Object.isSealed`|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.isSealed`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.IsFrozen, fonction](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Fonction Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)