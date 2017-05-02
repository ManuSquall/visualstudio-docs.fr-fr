---
title: "propertyIsEnumerable, m&#233;thode (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable (propriété)"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable, m&#233;thode (Object) (JavaScript)
Détermine si une propriété spécifiée est énumérable.  
  
## Syntaxe  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## Paramètres  
 `object`  
 Obligatoire.  Instance d'un objet.  
  
 `proName`  
 Obligatoire.  Valeur de chaîne du nom d'une propriété.  
  
## Notes  
 La méthode `propertyIsEnumerable` retourne `true` si `proName` existe dans `object` et peut être énuméré à l'aide d'une boucle `For`.  La méthode `propertyIsEnumerable` retourne la valeur `false` si `object` ne possède pas de propriété du nom spécifié ou si la propriété spécifiée n'est pas énumérable.  En règle générale, les propriétés prédéfinies ne sont pas énumérables, toutefois, celles qui sont définies par l'utilisateur le sont toujours.  
  
 La méthode `propertyIsEnumerable` ne prend pas en compte les objets dans la chaîne prototype.  
  
## Exemple  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [prototype, propriété \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)