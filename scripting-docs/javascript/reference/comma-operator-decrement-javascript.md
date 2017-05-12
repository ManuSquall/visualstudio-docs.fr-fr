---
title: "comma, op&#233;rateur (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "virgule (opérateur)"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# comma, op&#233;rateur (,) (JavaScript)
Entraîne l'exécution séquentielle de deux expressions.  
  
## Syntaxe  
  
```  
  
expression1, expression2  
```  
  
## Paramètres  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## Notes  
 L'opérateur `,` entraîne l'exécution des expressions de gauche à droite.  L'opérateur `,` est souvent utilisé dans l'expression d'incrémentation d'une boucle `for`.  Par exemple :  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 L'instruction `for` autorise l'exécution d'une seule expression à la fin de chaque passage dans la boucle.  L'opérateur `,` permet de traiter plusieurs expressions comme une expression simple. De cette manière, les deux variables peuvent être incrémentées.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)