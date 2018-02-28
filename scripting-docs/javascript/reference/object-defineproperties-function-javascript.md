---
title: Object.defineproperties, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties, fonction (JavaScript)
Ajoute une ou plusieurs propriétés à un objet et/ou modifie les attributs des propriétés existantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet sur lequel ajouter ou modifier les propriétés. Cela peut être natif [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet ou un objet DOM.  
  
 `descriptors`  
 Obligatoire. A [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet qui contient un ou plusieurs objets de descripteur. Chaque objet de descripteur décrit une propriété de données ou une propriété d’accesseur.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet qui a été passé à la fonction.  
  
## <a name="remarks"></a>Remarques  
 Le `descriptors` argument est un objet qui contient un ou plusieurs objets de descripteur.  
  
 A *propriété données* est une propriété qui peut stocker et récupérer une valeur. Un descripteur de propriété de données contient un `value` attribut, un `writable` , ou les deux. Pour plus d’informations, consultez [propriétés de données et des propriétés d’accesseur](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Un *propriété d’accesseur* appelle une fonction fournis par l’utilisateur chaque fois que la valeur de propriété est définie ou récupérée. Un descripteur de propriété d’accesseur contient un `set` attribut, un `get` , ou les deux.  
  
 Si l’objet a déjà une propriété qui porte le nom spécifié, les attributs de propriété sont modifiées. Pour plus d’informations, consultez [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Pour créer un objet et ajouter des propriétés pour le nouvel objet, vous pouvez utiliser la [Object.Create, fonction](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Ajout de propriétés  
 Dans l’exemple suivant, la `Object.defineProperties` fonction ajoute une propriété de données et une propriété d’accesseur à un objet défini par l’utilisateur.  
  
 L’exemple utilise un littéral d’objet pour créer le `descriptors` de l’objet avec la `newDataProperty` et `newAccessorProperty` objets du descripteur.  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Comme l’exemple précédent, l’exemple suivant ajoute des propriétés dynamiquement plutôt qu’avec un littéral d’objet.  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>Modification des propriétés  
 Pour modifier les attributs de propriété pour l’objet, ajoutez le code suivant. Le `Object.defineProperties` fonction modifie le `writable` attribut de `newDataProperty`et modifie le `enumerable` attribut de `newAccessorProperty`. Il ajoute `anotherDataProperty` à l’objet, car le nom de cette propriété n’existe pas déjà.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Spécifications  
 Prise en charge dans les normes Internet Explorer 9, des normes Internet Explorer 10, et [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] applications. Prise en charge dans Internet Explorer 8 pour les objets DOM uniquement, sinon ne pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getownpropertynames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.DefineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.Create, fonction](../../javascript/reference/object-create-function-javascript.md)   
 [Objet Object](../../javascript/reference/object-object-javascript.md)