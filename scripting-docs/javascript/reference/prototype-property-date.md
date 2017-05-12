---
title: "prototype, propri&#233;t&#233; (Date) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype, propri&#233;t&#233; (Date)
Retourne une référence au prototype d'une date.  
  
## Syntaxe  
  
```  
  
date.prototype  
```  
  
## Notes  
 L'argument `date` est le nom d'un objet.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une date.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Date` qui retourne la valeur du plus grand élément du tableau, déclarez la fonction, ajoutez\-la à `Date.prototype`, puis utilisez\-la.  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques ont une propriété `prototype` qui est en lecture seule.  Vous pouvez ajouter des propriétés et des méthodes au prototype, mais vous ne pouvez pas assigner un autre prototype à l'objet.  Toutefois, un nouveau prototype peut être assigné aux objets définis par l'utilisateur.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]