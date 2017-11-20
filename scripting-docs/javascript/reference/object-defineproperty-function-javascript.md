---
title: Object.DefineProperty, fonction (JavaScript) | Documents Microsoft
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
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty, fonction (JavaScript)
Ajoute une propriété à un objet ou modifie les attributs d'une propriété existante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet sur lequel ajouter ou modifier la propriété. Il peut s'agir d'un objet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] natif (un objet défini par l'utilisateur ou un objet intégré) ou bien d'un objet DOM.  
  
 `propertyname`  
 Obligatoire. Chaîne qui contient le nom de la propriété.  
  
 `descriptor`  
 Obligatoire. Descripteur de la propriété. Il peut être utilisé pour une propriété de données ou une propriété Accessor.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet modifié.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la fonction `Object.defineProperty` pour effectuer les opérations suivantes :   
  
-   Ajouter une nouvelle propriété à un objet. Cela se produit quand le nom de la propriété de l'objet n'est pas spécifié.  
  
-   Modifier les attributs d'une propriété existante. Cela se produit quand le nom de la propriété de l'objet est déjà spécifié.  
  
 La définition de propriété est fournie dans un objet descripteur, qui décrit les attributs d’une propriété de données ou d’une propriété Accessor. L'objet descripteur est un paramètre de la fonction `Object.defineProperty`.  
  
 Pour ajouter plusieurs propriétés à un objet, ou pour modifier plusieurs propriétés existantes, vous pouvez utiliser la [Object.defineproperties, fonction](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Exceptions  
 Une exception `TypeError` est levée si l'une des conditions suivantes a la valeur true :   
  
-   L'argument `object` n'est pas un objet.  
  
-   L’objet n’est pas [extensible](../../javascript/reference/object-isextensible-function-javascript.md) et le nom de propriété spécifié n’existe pas...  
  
-   Le `descriptor` a un attribut `value` ou `writable`, et un attribut `get` ou `set`.  
  
-   Le `descriptor` a un attribut `get` ou `set` qui n'est pas une fonction ou qui n'est pas non défini.  
  
-   Le nom de la propriété spécifié existe déjà, la propriété existante a un attribut `configurable` de valeur égale à `false`, et le `descriptor` contient un ou plusieurs attributs différents de ceux de la propriété existante. Toutefois, quand la propriété existante a un attribut `configurable` de valeur égale à `false` et un attribut `writable` de valeur égale à `true`, l'attribut `value` ou `writable` peut être différent.  
  
## <a name="adding-a-data-property"></a>Ajouter une propriété de données  
 Dans l'exemple suivant, la fonction `Object.defineProperty` ajoute une propriété de données à un objet défini par l'utilisateur. Pour ajouter plutôt la propriété à un objet DOM existant, supprimez les commentaires de la ligne `var = window.document`.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Pour répertorier les propriétés d'objet, ajoutez le code suivant à cet exemple.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Modification d'une propriété des données  
 Pour modifier un attribut de propriété pour l'objet, ajoutez le code suivant à la fonction `addDataProperty` illustrée précédemment. Le paramètre `descriptor` contient uniquement un attribut `writable`. Les autres attributs de propriété de données restent inchangés.  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>Ajouter une propriété d'accesseur  
 Dans l'exemple suivant, la fonction `Object.defineProperty` ajoute une propriété d'accesseur à un objet défini par l'utilisateur.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Pour répertorier les propriétés d'objet, ajoutez le code suivant à cet exemple.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>Modification d'une propriété d'accesseur  
 Pour modifier un attribut de propriété pour l'objet, ajoutez le code suivant au code illustré précédemment. Le paramètre `descriptor` contient uniquement une définition de l'accesseur `get`. Les autres attributs de propriété restent inchangés.  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>Modification d'une propriété sur un élément DOM  
 L'exemple suivant montre comment personnaliser des propriétés DOM intégrées à l'aide de la fonction `Object.getOwnPropertyDescriptor` afin d'obtenir et de modifier le descripteur de propriété de la propriété. Pour cet exemple, il doit exister un élément DIV avec l'ID « div ».  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>Spécifications  
 Internet Explorer 9 (mode normes) et Internet Explorer 10 (mode normes) ainsi que les applications du [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] prennent en charge toutes les fonctionnalités.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] prend en charge les objets DOM, mais pas les objets définis par l'utilisateur. Les attributs `enumerable` et `configurable` peuvent être spécifiés, mais ils ne sont pas utilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Document prototypes DOM, partie 2 : Accesseur (accesseur Get/Set) prise en charge](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineproperties, fonction](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.Create, fonction](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Fonction Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)