---
title: "for, instruction (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "structures de boucle, instructions for"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for, instruction (JavaScript)
Exécute un bloc d'instructions for tant qu'une condition spécifiée a la valeur true.  
  
## Syntaxe  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## Paramètres  
 `initialization`  
 Facultatif.  Expression.  Cette expression est exécutée une seule fois, avant l'exécution de la boucle.  
  
 `test`  
 Facultatif.  Expression booléenne.  Si le `test` a la valeur `true`, `statement` est exécutée.  Si le `test` a la valeur `false`, la boucle prend fin.  
  
 `increment`  
 Facultatif.  Expression.  L'expression d'incrémentation est exécutée à la fin de chaque passage dans la boucle.  
  
 `statement`  
 Facultatif.  Une ou plusieurs instructions doivent être exécutées si le `test` a la valeur **true**.  Il peut s'agir d'une instruction composée.  
  
## Notes  
 En général, une instruction `for` est utilisée lorsqu'une boucle doit être exécutée un nombre de fois déterminé.  Une boucle `for` permet d'itérer une instruction au sein de tableaux et d'effectuer des traitements séquentiels.  
  
 Le test d'une expression conditionnelle a lieu avant l'exécution de la boucle. En conséquence, une instruction `for` est exécutée plusieurs fois ou pas du tout.  
  
 Sur toute ligne d'un bloc d'instructions de boucle `for`, utilisez l'instruction `break` pour quitter la boucle ou l'instruction `continue` pour transférer le contrôle à l'itération suivante de la boucle.  
  
## Exemple  
 Dans l'exemple suivant, l'instruction `for` exécute les instructions délimitées comme suit :  
  
-   En premier lieu, la valeur initiale de la variable `i` est évaluée.  
  
-   Ensuite, tant que la valeur de `i` est inférieure ou égale à 9, les instructions `document.write` sont exécutées et la variable `i` est réévaluée.  
  
-   Lorsque la variable `i` est supérieure à 9, la condition prend la valeur false et le contrôle est transféré hors de la boucle.  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## Exemple  
 Toutes les expressions de l'instruction `for` sont facultatives.  Dans l'exemple suivant, les instructions `for` génèrent une boucle infinie et une instruction `break` est utilisée pour quitter la boucle.  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)