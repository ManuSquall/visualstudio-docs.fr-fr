---
title: "prototype, propri&#233;t&#233; (String) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype, propri&#233;t&#233; (String)
Retourne une référence au prototype d'une classe de chaîne.  
  
## Syntaxe  
  
```  
  
string.prototype  
```  
  
## Notes  
 L'argument `string` est le nom d'une chaîne.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `String` qui retourne la valeur du dernier élément de la chaîne, déclarez la fonction, ajoutez\-la à `String.prototype`, puis utilisez\-la.  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques ont une propriété `prototype` qui est en lecture seule.  Vous pouvez ajouter des propriétés et des méthodes au prototype, mais vous ne pouvez pas assigner un autre prototype à l'objet.  Toutefois, un nouveau prototype peut être assigné aux objets définis par l'utilisateur.  
  
 Les listes de méthodes et de propriétés reprises dans ce guide de référence du langage indiquent, pour chaque objet intrinsèque, lesquelles appartiennent au prototype de l'objet et lesquelles n'en font pas partie.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]