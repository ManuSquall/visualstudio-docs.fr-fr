---
title: "propertyIsEnumerable, méthode (Object) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable, méthode (Object) (JavaScript)
Détermine si une propriété spécifiée est énumérable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Instance d’un objet.  
  
 `proName`  
 Obligatoire. Valeur de chaîne d’un nom de propriété.  
  
## <a name="remarks"></a>Remarques  
 Le `propertyIsEnumerable` méthode retourne `true` si `proName` existe dans `object` et peuvent être énumérés à l’aide un `For` boucle. Le `propertyIsEnumerable` méthode retourne `false` si `object` ne dispose pas d’une propriété portant le nom spécifié ou si la propriété spécifiée n’est pas énumérable. En règle générale, les propriétés prédéfinies ne peuvent pas être énumérées, mais les propriétés définies par l’utilisateur sont toujours énumérables.  
  
 Le `propertyIsEnumerable` méthode ne considère pas les objets dans la chaîne prototype.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)