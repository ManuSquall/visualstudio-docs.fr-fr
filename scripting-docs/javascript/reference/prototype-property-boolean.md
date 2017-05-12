---
title: "prototype, propri&#233;t&#233; (Boolean) | Microsoft Docs"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype, propri&#233;t&#233; (Boolean)
Retourne une référence au prototype pour un booléen.  
  
## Syntaxe  
  
```  
  
boolean.prototype  
```  
  
## Notes  
 L'argument `boolean` est le nom d'un objet.  
  
 La propriété `prototype` fournit un ensemble de base de fonctionnalités à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  Les propriétés et les méthodes peuvent être ajoutées au prototype, mais un prototype différent ne peut pas être assigné aux objets incorporés.  
  
 Par exemple, pour ajouter une méthode à l'objet `Boolean` qui retourne la valeur de l'élément le plus volumineux du tableau, déclarez la fonction, ajoutez\-la à `Boolean.prototype`, et réutilisez\-la.  
  
```javascript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]