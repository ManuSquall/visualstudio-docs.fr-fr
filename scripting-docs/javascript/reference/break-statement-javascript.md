---
title: "break, instruction (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break (instruction)"
  - "do...while (instruction)"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break, instruction (JavaScript)
Termine la boucle en cours ou, si elle est utilisée en conjonction avec l'argument `label`, termine l'instruction associée.  
  
## Syntaxe  
  
```  
break [label];  
```  
  
## Notes  
 L'argument `label` facultatif spécifie l'étiquette de l'instruction que vous interrompez.  
  
 L'instruction `break` est généralement utilisée dans les instructions `switch` et dans les boucles `while`, `for`, `for...in` ou `do...while`.  La plupart du temps, l'argument `label` est utilisé dans les instructions `switch`, mais vous pouvez l'utiliser dans n'importe quelle instruction, qu'elle soit simple ou composée.  
  
 L'exécution de l'instruction `break` permet de quitter la boucle ou l'instruction en cours et commence l'exécution du script avec l'instruction qui suit immédiatement.  
  
## Exemples  
 Dans l'exemple suivant, le compteur est configuré pour compter de 1 à 99 ; toutefois, l'instruction `break` termine la boucle lorsque la valeur du compteur atteint 14.  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Dans le code suivant, l'instruction `break` fait référence à la boucle `for` précédée de l'instruction `Inner:`.  Lorsque `j` est égal à 24, l'instruction `break` force le flux du programme à quitter cette boucle.  Les nombres 21 à 23 s'impriment sur chaque ligne.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [Instruction do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled, instruction](../../javascript/reference/labeled-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)