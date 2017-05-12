---
title: "prototype, propri&#233;t&#233; (Error) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype, propri&#233;t&#233; (Error)
Retourne une référence au prototype d'une erreur.  
  
## Syntaxe  
  
```  
  
error.prototype  
```  
  
## Notes  
 L'argument `error` est le nom d'une erreur.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une erreur.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Error` qui retourne la valeur du plus grand élément du tableau, déclarez la fonction, ajoutez\-la à `Error.prototype`, puis utilisez\-la.  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques ont une propriété `prototype` qui est en lecture seule.  Vous pouvez ajouter des propriétés et des méthodes au prototype, mais vous ne pouvez pas assigner un autre prototype à l'objet.  Toutefois, un nouveau prototype peut être assigné aux objets définis par l'utilisateur.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]