---
title: Object.Seal, fonction (JavaScript) | Documents Microsoft
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641149"
---
# <a name="objectseal-function-javascript"></a>Object.seal, fonction (JavaScript)
Empêche la modification des attributs des propriétés existantes et empêche l'ajout de nouvelles propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. L’objet sur lequel les attributs de verrouillage.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet qui est passé à la fonction.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `Object.seal` fonction effectue les actions suivantes :  
  
-   Rend l’objet non extensible afin que les nouvelles propriétés ne peuvent pas être ajoutées à ce dernier.  
  
-   Définit le `configurable` attribut `false` pour toutes les propriétés de l’objet.  
  
 Lorsque le `configurable` attribut est `false`, les attributs de propriété ne peut pas être modifiés et la propriété ne peut pas être supprimée. Lorsque `configurable` est `false` et `writable` est `true`, le `value` et `writable` attributs peuvent être modifiés.  
  
 Le `Object.seal` fonction ne modifie pas le `writable` attribut.  
  
 Pour plus d’informations sur la façon de définir les attributs de propriété, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md). Pour obtenir les attributs d’une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Les fonctions associées suivantes empêchent la modification des attributs d’objet.  
  
|Fonction|Objet devient non extensible|`configurable`a la valeur `false` pour chaque propriété.|`writable`a la valeur `false` pour chaque propriété.|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|`Object.seal`|Oui|Oui|Non|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Ces fonctions retournent `true` si toutes les conditions sont marqués dans le tableau suivant sont remplies.  
  
|Fonction|Objet est extensible ?|`configurable`est `false` pour toutes les propriétés ?|`writable`est `false` pour toutes les propriétés de données ?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.seal`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.Freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.IsSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Fonction Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)