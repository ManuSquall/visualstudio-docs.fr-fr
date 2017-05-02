---
title: "XOR, op&#233;rateur d&#39;assignation de bits (^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= (opérateur)"
  - "^= (opérateur), à propos de l'opérateur ^="
  - "opérateurs d'assignation, de bits (JavaScript)"
  - "opérateurs de bits, XOR (opérateur)"
  - "XOR (opérateur)"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# XOR, op&#233;rateur d&#39;assignation de bits (^=) (JavaScript)
Effectue une opération de bits OR exclusive sur une variable et une expression puis assigne le résultat à la variable.  
  
## Syntaxe  
  
```  
  
result ^= expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 Utiliser l'opérateur **^\=** revient exactement à spécifier :  
  
```javascript  
result = result ^ expression  
```  
  
 L'opérateur **^** examine la représentation binaire des valeurs de deux expressions et effectue une opération de bits OR exclusive sur celles\-ci.  Le résultat de cette opération est le suivant :  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Si une et seulement une des expressions comporte un 1, le résultat comporte un 1.  Sinon, le résultat comporte un 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [^, opérateur de bits XOR](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)