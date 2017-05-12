---
title: "do...while, instruction (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while (instruction)"
  - "terminer les boucles"
  - "structures de boucle, do et do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while, instruction (JavaScript)
Exécute un bloc d'instructions une première fois, puis répète l'exécution de la boucle jusqu'à ce qu'une expression de condition prenne la valeur `false`.  
  
## Syntaxe  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Paramètres  
 `statement`  
 Requis.  Instruction à exécuter si `expression` a la valeur `true`.  Il peut s'agir d'une instruction composée.  
  
 `expression`  
 Requis.  Expression pouvant être convertie en valeur booléenne `true` ou `false`.  Si le paramètre `expression` a la valeur `true`, la boucle est à nouveau exécutée.  Si le paramètre `expression` a la valeur `false`, la boucle est terminée.  
  
## Notes  
 Contrairement à l'instruction `while`, une boucle `do...while` est exécutée une fois avant que l'expression conditionnelle ne soit évaluée.  
  
 Sur toute ligne d'un bloc `do…while`, vous pouvez utiliser l'instruction `break` pour forcer le flux du programme à quitter la boucle ou l'instruction `continue` pour passer directement à l'expression `while`.  
  
## Exemple  
 Dans l'exemple suivant, les instructions de la boucle `do...while` continuent à s'exécuter tant que la variable `i` est inférieure à 10.  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## Exemple  
 Dans l'exemple suivant, les instructions à l'intérieur de la boucle sont exécutées une fois même si la condition n'est pas remplie.  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)   
 [Labeled, instruction](../../javascript/reference/labeled-statement-javascript.md)