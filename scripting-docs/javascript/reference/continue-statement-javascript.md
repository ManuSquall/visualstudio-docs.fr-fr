---
title: "continue, instruction (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (instruction)"
  - "do...while (instruction)"
  - "structures de boucle, continue (instruction)"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue, instruction (JavaScript)
Arrête l'itération en cours d'une boucle, et en lance une nouvelle.  
  
## Syntaxe  
  
```  
continue [label];  
```  
  
## Notes  
 L'argument facultatif `label` spécifie l'instruction à laquelle `continue` s'applique.  
  
 Vous pouvez uniquement utiliser l'instruction `continue` à l'intérieur d'une boucle `while`, `do...while`, **for** ou `for...in`.  L'exécution de l'instruction `continue` arrête l'itération de la boucle en cours et poursuit le déroulement du programme au début de la boucle.  Cette action a des conséquences différentes selon les types de boucles :  
  
-   Les boucles `while` et `do...while` testent leur condition et, si celle\-ci se vérifie \(true\), elles exécutent une nouvelle fois la boucle.  
  
-   Les boucles `for` exécutent leur expression d'incrémentation et, si le test se vérifie \(true\), elles exécutent une nouvelle fois la boucle.  
  
-   Les boucles `for...in` passent au champ suivant de la variable spécifiée et exécutent une nouvelle fois la boucle.  
  
## Exemples  
 Dans cet exemple, une boucle itère de 1 à 9.  Les instructions entre `continue` et la fin du corps de `for` sont ignorées à cause de l'utilisation de l'instruction `continue` avec l'expression `(i < 5)`.  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Dans le code suivant, l'instruction `continue` fait référence à la boucle `for` précédée de l'étiquette `Inner:`.  Lorsque `j` est égal à 24, l'instruction `continue` force la boucle `for` à passer à l'itération suivante.  Les nombres 21 à 23 et 25 à 30 s'impriment sur chaque ligne.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Instruction do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled, instruction](../../javascript/reference/labeled-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)