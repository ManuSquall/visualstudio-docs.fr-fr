---
title: "const, instruction (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "déclaration de variables, instruction const"
  - "const (instruction)"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const, instruction (JavaScript)
Déclare une variable ayant une portée de bloc avec une valeur de constante.  
  
## Syntaxe  
  
```  
const constant1 = value1  
```  
  
#### Paramètres  
 `constant1`  
 Nom de la variable en cours de déclaration.  
  
 `value1`  
 Valeur initiale assignée à la variable.  
  
## Notes  
 Utilisez l'instruction `const` pour déclarer une variable avec une valeur constante, dont la portée est limitée au bloc dans lequel elle est déclarée.  La valeur de la variable ne peut pas être modifiée.  
  
 Une variable déclarée avec `const` doit être initialisée lorsqu'elle est déclarée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `const`.  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Instruction let](../../javascript/reference/let-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)