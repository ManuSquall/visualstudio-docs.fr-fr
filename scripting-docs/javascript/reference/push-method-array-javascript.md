---
title: "push, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push (méthode)"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push, m&#233;thode (Array) (JavaScript)
Ajoute de nouveaux éléments à un tableau et retourne la nouvelle longueur du tableau.  
  
## Syntaxe  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Objet `Array`.  
  
 `item, item2,. . ., itemN`  
 Facultatif.  Nouveaux éléments de l'objet `Array`.  
  
## Notes  
 Les méthodes `push` et `pop` vous permettent de simuler une pile de type dernier entré, premier sorti.  
  
 La méthode `push` ajoute les éléments dans l'ordre de leur apparition.  Si l'un des arguments est un tableau, il est ajouté en tant qu'élément unique.  Utilisez la méthode `concat` pour joindre les éléments issus de plusieurs tableaux.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `push`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Méthode concat \(tableau\)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop, méthode \(Array\)](../../javascript/reference/pop-method-array-javascript.md)