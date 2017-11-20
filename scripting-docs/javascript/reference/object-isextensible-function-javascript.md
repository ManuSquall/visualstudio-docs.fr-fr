---
title: Object.isextensible, fonction (JavaScript) | Documents Microsoft
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
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectisextensible-function-javascript"></a>Object.isExtensible, fonction (JavaScript)
Retourne une valeur qui indique si de nouvelles propriétés peuvent être ajoutées à un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si l’objet est extensible, ce qui indique que les nouvelles propriétés peuvent être ajoutées à l’objet ; dans le cas contraire, `false`.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
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
|`Object.isExtensible`|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.isExtensible`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.IsSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Fonction Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)