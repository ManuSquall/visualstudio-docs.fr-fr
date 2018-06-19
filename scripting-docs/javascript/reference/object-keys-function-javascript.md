---
title: Object.Keys, fonction (JavaScript) | Documents Microsoft
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639749"
---
# <a name="objectkeys-function-javascript"></a>Object.keys, fonction (JavaScript)
Retourne les noms des propriétés et méthodes énumérables d'un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`object`|Obligatoire. Objet qui contient les propriétés et méthodes. Il peut s’agir d’un objet que vous avez créé ou un objet de modèle DOM (Document Object) existant.|  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau qui contient les noms des propriétés énumérables et les méthodes de l’objet.  
  
## <a name="exceptions"></a>Exceptions  
 Si la valeur fournie pour le `object` argument n’est pas le nom d’un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `keys` méthode retourne uniquement les noms des méthodes et propriétés énumérables. Pour retourner les noms de propriétés énumérables et non énumérable et méthodes, vous pouvez utiliser [Object.getownpropertynames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Pour plus d’informations sur la `enumerable` attribut d’une propriété, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md) et [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un objet qui possède trois propriétés et une méthode. Il utilise ensuite la `keys` méthode pour obtenir les propriétés et méthodes de l’objet.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les noms de toutes les propriétés énumérables qui commencent par la lettre « g » dans l’objet de pâtes.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)