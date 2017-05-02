---
title: "let, instruction (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let (instruction)"
  - "déclarer des variables, instruction let"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let, instruction (JavaScript)
Déclare une variable avec une portée de bloc.  
  
## Syntaxe  
  
```  
let variable1 = value1  
```  
  
#### Paramètres  
 `variable1`  
 Nom de la variable en cours de déclaration.  
  
 `value1`  
 Valeur initiale assignée à la variable.  
  
## Notes  
 Utilisez l'instruction `let` pour déclarer une variable, dont la portée est limitée au bloc dans lequel elle est déclarée.  Vous pouvez assigner des valeurs aux variables au moment de leur déclaration ou ultérieurement dans votre script.  
  
 Une variable déclarée avec `let` ne peut pas être utilisée avant sa déclaration. Sinon, une erreur se produit.  
  
 Si vous n'initialisez pas votre variable dans l'instruction `let`, la valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] `undefined` lui est automatiquement attribuée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `let`.  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Instruction const](../../javascript/reference/const-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)