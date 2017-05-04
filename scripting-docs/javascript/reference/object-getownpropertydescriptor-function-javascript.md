---
title: "Object.getOwnPropertyDescriptor, fonction (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyDescriptor (méthode) (JavaScript)"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Object.getOwnPropertyDescriptor, fonction (JavaScript)
Obtient le propre descripteur de propriété de l'objet spécifié.  Le propre descripteur de propriété est un descripteur qui est défini directement sur l'objet et non hérité du prototype de l'objet.  
  
## Syntaxe  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## Paramètres  
 `object`  
 Obligatoire.  Objet qui contient la propriété.  
  
 `propertyname`  
 Obligatoire.  Nom de la propriété.  
  
## Valeur de retour  
 Descripteur de la propriété.  
  
## Notes  
 Vous pouvez utiliser la fonction `Object.getOwnPropertyDescriptor` pour obtenir un objet descripteur qui décrit les attributs de la propriété.  
  
 La [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md) est utilisée pour ajouter ou modifier des propriétés.  
  
## Exemple de propriété de données  
 L'exemple suivant obtient un descripteur de propriété de données et l'utilise pour mettre la propriété en lecture seule.  
  
```javascript  
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
  
```javascript  
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
  
## Configuration requise  
 Toutes les fonctionnalités sont prises en charge dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] prend en charge les objets DOM, mais pas les objets définis par l'utilisateur.  Les attributs `enumerable` et `configurable` peuvent être spécifiés, mais ils ne sont pas utilisés.  
  
## Voir aussi  
 [Prototypes DOM, partie 2 : prise en charge d'accesseurs \(Get\/Set\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty, fonction](../../javascript/reference/object-defineproperty-function-javascript.md)