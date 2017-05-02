---
title: "while, instruction (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "structures de boucle, instructions while"
  - "while, instruction"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while, instruction (JavaScript)
Exécute une instruction ou une série d'instructions jusqu'à ce qu'une condition spécifiée ait la valeur `false`.  
  
## Syntaxe  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Paramètres  
 `expression`  
 Requis.  Expression booléenne vérifiée avant chaque itération de la boucle.  Si le paramètre `expression` a la valeur `true`, la boucle est exécutée.  Si le paramètre `expression` a la valeur `false`, la boucle est terminée.  
  
 `statements`  
 Optionnel.  Une ou plusieurs instructions à exécuter si `expression` a la valeur `true`.  
  
## Notes  
 L'instruction `while` vérifie l'argument `expression` avant d'exécuter pour la première fois une boucle.  Si le paramètre `expression` a la valeur `false` à ce moment là, la boucle n'est jamais exécutée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `while`.  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [Instruction do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)