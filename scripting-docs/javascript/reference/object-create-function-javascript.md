---
title: Object.Create, fonction (JavaScript) | Documents Microsoft
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640479"
---
# <a name="objectcreate-function-javascript"></a>Object.create, fonction (JavaScript)
Crée un objet qui a le prototype spécifié et qui contient éventuellement des propriétés spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prototype`  
 Obligatoire. Objet à utiliser comme un prototype. Peut avoir la valeur `null`.  
  
 `descriptors`  
 Facultatif. A [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet qui contient un ou plusieurs descripteurs de propriété.  
  
 Une *propriété de données* est une propriété qui peut obtenir et définir une valeur. Un descripteur de propriété de données contient un `value` attribut, ainsi que `writable`, `enumerable`, et `configurable` attributs. Si les trois derniers attributs ne sont pas spécifiées, leur valeur par défaut `false`. Un *propriété d’accesseur* appelle une fonction fournis par l’utilisateur chaque fois que la valeur à récupérer ou à définir. Un descripteur de propriété d’accesseur contient un `set` attribut, un `get` , ou les deux. Pour plus d’informations, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Un nouvel objet qui a le prototype interne spécifié et contient les propriétés spécifiées, le cas échéant.  
  
## <a name="exceptions"></a>Exceptions  
 A `TypeError` exception est levée si une des conditions suivantes est vraie :  
  
-   Le `prototype` argument n’est pas un objet et n’est pas `null`.  
  
-   Un descripteur dans le `descriptors` argument a une `value` ou `writable` et un `get` ou `set` attribut.  
  
-   Un descripteur dans le `descriptors` argument a une `get` ou `set` attribut qui n’est pas une fonction.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser cette fonction à l’aide un `null``prototype` paramètre afin d’arrêter la chaîne prototype. L’objet créé n’aura aucun prototype.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un objet en utilisant un `null` prototype et ajoute deux propriétés énumérables.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un objet qui a le même prototype interne en tant que l’objet. Vous pouvez voir qu’il a le même prototype sous la forme d’un objet créé à l’aide d’un littéral d’objet. Le [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) fonction obtient le prototype de l’objet d’origine. Pour obtenir le descripteur de propriété de l’objet, vous pouvez utiliser [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un objet qui a le même prototype interne en tant que l’objet forme.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Object.getprototypeof, fonction](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf, méthode (objet)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Création d'objets](../../javascript/creating-objects-javascript.md)