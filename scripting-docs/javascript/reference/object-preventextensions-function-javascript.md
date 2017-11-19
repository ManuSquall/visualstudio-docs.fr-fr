---
title: Object.preventextensions, fonction (JavaScript) | Documents Microsoft
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
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Object.preventExtensions, fonction (JavaScript)
Empêche l'ajout de nouvelles propriétés à un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet à rendre non extensible.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet qui est passé à la fonction.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `Object.preventExtensions` fonction rend un objet non extensible afin que les nouvelles propriétés de nommé ne peut pas être ajoutées à ce dernier. Après avoir effectué un objet non extensible, elle ne peut pas être rendue extensible.  
  
 Pour plus d’informations sur la façon de définir les attributs de propriété, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Les fonctions associées suivantes empêchent la modification des attributs d’objet.  
  
|Fonction|Objet devient non extensible|`configurable`a la valeur `false` pour chaque propriété.|`writable`a la valeur `false` pour chaque propriété.|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Oui|Non|Non|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Oui|Oui|Oui|  
  
 Ces fonctions retournent `true` si toutes les conditions sont marqués dans le tableau suivant sont remplies.  
  
|Fonction|Objet est extensible ?|`configurable`est `false` pour toutes les propriétés ?|`writable`est `false` pour toutes les propriétés de données ?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Non|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.preventExtensions`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.Seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.IsSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Fonction Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)