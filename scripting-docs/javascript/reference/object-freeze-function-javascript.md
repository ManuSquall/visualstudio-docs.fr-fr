---
title: Object.Freeze, fonction (JavaScript) | Documents Microsoft
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze, fonction (JavaScript)
Empêche la modification des attributs et valeurs de propriété existants, et empêche l'ajout de nouvelles propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. L’objet sur lequel les attributs de verrouillage.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet qui est passé à la fonction.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `object` argument n’est pas un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `Object.freeze` fonction effectue les opérations suivantes :  
  
-   Rend l’objet non extensible afin que les nouvelles propriétés ne peuvent pas être ajoutées à ce dernier.  
  
-   Définit le `configurable` attribut `false` pour toutes les propriétés de l’objet. Lorsque `configurable` est `false`, les attributs de propriété ne peut pas être modifiés et que la propriété ne peut pas être supprimée.  
  
-   Définit le `writable` attribut `false` pour toutes les propriétés de données de l’objet. Lorsque `writable` a la valeur false, la valeur de propriété de données ne peut pas être modifiée.  
  
 Pour plus d’informations sur la façon de définir les attributs de propriété, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md). Pour obtenir les attributs d’une propriété, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Les fonctions associées suivantes empêchent la modification des attributs d’objet.  
  
|Fonction|Objet devient non extensible|`configurable`a la valeur `false` pour chaque propriété.|`writable`a la valeur `false` pour chaque propriété.|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Oui|Non|Non|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Oui|Oui|Non|  
|`Object.freeze`|Oui|Oui|Oui|  
  
 Ces fonctions retournent `true` si toutes les conditions sont marqués dans le tableau suivant sont remplies.  
  
|Fonction|Objet est extensible ?|`configurable`est `false` pour toutes les propriétés ?|`writable`est `false` pour toutes les propriétés de données ?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Oui|Non|Non|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Non|Oui|Oui|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Non|Oui|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Object.freeze`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal, fonction](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isextensible, fonction](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.IsSealed, fonction](../../javascript/reference/object-issealed-function-javascript.md)   
 [Fonction Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)