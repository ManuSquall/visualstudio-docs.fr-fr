---
title: "prototype, propri&#233;t&#233; (Number) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype, propri&#233;t&#233; (Number)
Retourne une référence au prototype d'une classe de nombre.  
  
## Syntaxe  
  
```  
  
number.prototype  
```  
  
## Notes  
 L'argument `number` est le nom d'un nombre.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Number` qui retourne le nombre de chiffres \(entiers\), déclarez la fonction, ajoutez\-la à `Number.prototype`, puis utilisez\-la.  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques ont une propriété `prototype` qui est en lecture seule.  Vous pouvez ajouter des propriétés et des méthodes au prototype, mais vous ne pouvez pas assigner un autre prototype à l'objet.  Toutefois, un nouveau prototype peut être assigné aux objets définis par l'utilisateur.  
  
 Les listes de méthodes et de propriétés reprises dans ce guide de référence du langage indiquent, pour chaque objet intrinsèque, lesquelles appartiennent au prototype de l'objet et lesquelles n'en font pas partie.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]