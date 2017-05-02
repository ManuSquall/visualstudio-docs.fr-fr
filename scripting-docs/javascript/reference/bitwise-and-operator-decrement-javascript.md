---
title: "AND, op&#233;rateur de bits (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs d’assignation, au niveau du bit (JavaScript)"
  - "& (opérateur), à propos de l’opérateur &"
  - "AND (opérateur)"
  - "& (opérateur)"
  - "opérateurs de bits, opérateur AND"
  - "& (opérateur), opérateurs de bits"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# AND, op&#233;rateur de bits (&amp;) (JavaScript)
Effectue une opération de bits AND sur deux expressions 32 bits.  
  
## Syntaxe  
  
```  
  
result = expression1 & expression2  
```  
  
## Paramètres  
 `result`  
 Résultat de l'opération.  
  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## Notes  
 `&` effectue une opération de bits AND sur chacun des bits des deux expressions 32 bits.  Si les deux bits ont la valeur 1, le résultat est 1.  Sinon, le résultat est 0.  
  
|Bit1|Bit2|Valeur de l'opération AND|  
|----------|----------|-------------------------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Les exemples suivants illustrent l'utilisation de l'opérateur `&`.  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Opérateur d'assignation de bits AND \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)