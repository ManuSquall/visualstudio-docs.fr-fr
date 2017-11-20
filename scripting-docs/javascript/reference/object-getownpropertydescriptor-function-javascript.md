---
title: Object.getOwnPropertyDescriptor, fonction (JavaScript) | Documents Microsoft
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
helpviewer_keywords: getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Object.getOwnPropertyDescriptor, fonction (JavaScript)
Obtient le propre descripteur de propriété de l'objet spécifié. Le propre descripteur de propriété est un descripteur qui est défini directement sur l'objet et non hérité du prototype de l'objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet qui contient la propriété.  
  
 `propertyname`  
 Obligatoire. Nom de la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Descripteur de la propriété.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la fonction `Object.getOwnPropertyDescriptor` pour obtenir un objet descripteur qui décrit les attributs de la propriété.  
  
 Le [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md) est utilisée pour ajouter ou modifier les propriétés.  
  
## <a name="data-property-example"></a>Exemple de propriété de données  
 L'exemple suivant obtient un descripteur de propriété de données et l'utilise pour mettre la propriété en lecture seule.  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Pour répertorier les attributs de propriété, vous pouvez ajouter le code suivant à cet exemple.  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>Spécifications  
 Toutes les fonctionnalités sont prises en charge dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] prend en charge les objets DOM, mais pas les objets définis par l'utilisateur. Les attributs `enumerable` et `configurable` peuvent être spécifiés, mais ils ne sont pas utilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Document prototypes DOM, partie 2 : Accesseur (accesseur Get/Set) prise en charge](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Fonction Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)