---
title: "prototype, propri&#233;t&#233; (Object) (JavaScript) | Microsoft Docs"
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
  - "Prototype"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "héritage, objets"
  - "Prototype (propriété)"
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# prototype, propri&#233;t&#233; (Object) (JavaScript)
Retourne une référence au prototype pour une classe d'objets.  
  
## Syntaxe  
  
```  
  
objectName.prototype  
```  
  
## Notes  
 L'argument `objectName` est le nom d'un objet.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Array` qui retourne la valeur du plus grand élément du tableau, déclarez la fonction, ajoutez\-la à `Array.prototype`, puis utilisez\-la.  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 Tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques ont une propriété `prototype` qui est en lecture seule.  Vous pouvez ajouter des propriétés et des méthodes au prototype, mais vous ne pouvez pas assigner un autre prototype à l'objet.  Toutefois, un nouveau prototype peut être assigné aux objets définis par l'utilisateur.  
  
 Les listes de méthodes et de propriétés reprises dans ce guide de référence du langage indiquent, pour chaque objet intrinsèque, lesquelles appartiennent au prototype de l'objet et lesquelles n'en font pas partie.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [constructor, propriété \(Object\)](../../javascript/reference/constructor-property-object-javascript.md)