---
title: "XOR, op&#233;rateur de bits (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs de bits, XOR (opérateur)"
  - "XOR (opérateur)"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# XOR, op&#233;rateur de bits (^) (JavaScript)
Effectue une opération de bits OR exclusive sur deux expressions.  
  
## Syntaxe  
  
```  
  
result = expression1 ^ expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 L'opérateur **^** examine la représentation binaire des valeurs de deux expressions et effectue une opération de bits OR exclusive sur celles\-ci.  Le résultat de cette opération est le suivant :  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Si une et seulement une des expressions comporte un 1, le résultat comporte un 1.  Sinon, le résultat comporte un 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [^\=, opérateur d'assignation de bits XOR](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)