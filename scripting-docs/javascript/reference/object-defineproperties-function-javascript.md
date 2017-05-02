---
title: "Object.defineProperties, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object.defineProperties (fonction) (JavaScript)"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties, fonction (JavaScript)
Ajoute une ou plusieurs propriétés à un objet et\/ou modifie les attributs des propriétés existantes.  
  
## Syntaxe  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Paramètres  
 `object`  
 Requis.  Objet sur lequel ajouter ou modifier les propriétés.  Il peut s'agir d'un objet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] natif ou d'un objet DOM.  
  
 `descriptors`  
 Requis.  Objet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui contient un ou plusieurs objets descripteurs.  Chaque objet descripteur décrit une propriété de données ou une propriété Accessor.  
  
## Valeur de retour  
 L'objet a été passé à la fonction.  
  
## Notes  
 L'argument `descriptors` est un objet qui contient un ou plusieurs objets descripteurs.  
  
 Une *propriété de données* est une propriété qui peut stocker et récupérer une valeur.  Un descripteur de propriété de données contient un attribut `value`, un attribut `writable` ou les deux.  Pour plus d'informations, consultez [Propriétés des données et propriétés des accesseurs](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Une *propriété Accessor* appelle une fonction fournie par l'utilisateur chaque fois que la valeur de la propriété est définie ou récupérée.  Un descripteur de propriété Accessor contient un attribut `set`, un attribut `get` ou les deux.  
  
 Si l'objet possède déjà une propriété qui porte le nom spécifié, les attributs de propriété sont modifiés.  Pour plus d'informations, consultez [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Pour créer un objet et lui ajouter des propriétés, vous pouvez utiliser [Object.create, fonction](../../javascript/reference/object-create-function-javascript.md).  
  
## Ajout de propriétés  
 Dans l'exemple suivant, la fonction `Object.defineProperties` ajoute une propriété de données et une propriété Accessor à un objet défini par l'utilisateur.  
  
 L'exemple utilise un littéral d'objet pour créer l'objet `descriptors` avec les objets descripteurs `newDataProperty` et `newAccessorProperty`.  
  
```javascript  
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
  
 Comme l'exemple précédent, l'exemple suivant ajoute les propriétés dynamiquement plutôt qu'avec un littéral d'objet.  
  
```javascript  
  
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
  
## Modification des propriétés  
 Pour modifier les attributs de propriété pour l'objet, ajoutez le code suivant.  La fonction `Object.defineProperties` modifie l'attribut `writable` de `newDataProperty` et modifie l'attribut `enumerable` de `newAccessorProperty`.  Elle ajoute `anotherDataProperty` à l'objet car ce nom de propriété n'existe pas encore.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## Configuration requise  
 Pris en charge dans Internet Explorer 9 \(mode standard\), Internet Explorer 10 \(mode standard\) et les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Pris en charge dans Internet Explorer 8 pour les objets DOM uniquement, non pris en charge dans les autres cas.  
  
## Voir aussi  
 [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames, fonction](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create, fonction](../../javascript/reference/object-create-function-javascript.md)   
 [Object, objet](../../javascript/reference/object-object-javascript.md)