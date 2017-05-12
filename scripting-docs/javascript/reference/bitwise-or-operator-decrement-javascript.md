---
title: "OR, op&#233;rateur de bits (|) (JavaScript) | Microsoft Docs"
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
  - "|"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "| (opérateur)"
  - "opérateurs de bits, OR (opérateur)"
  - "OR (opérateur)"
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# OR, op&#233;rateur de bits (|) (JavaScript)
Effectue une opération de bits OR sur deux expressions.  
  
## Syntaxe  
  
```  
  
result = expression1 | expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 L'opérateur          **&#124;** examine la représentation binaire des valeurs de deux expressions et effectue une opération de bits OR sur celles\-ci.  Le résultat de cette opération est le suivant :  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Lorsque l'une des expressions a un 1, le résultat comporte un 1.  Sinon, le résultat comporte un 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [&#124;\=, opérateur d'assignation de bits OR](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)