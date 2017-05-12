---
title: "OR, op&#233;rateur d&#39;assignation de bits (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= (opérateur)"
  - "opérateurs d'assignation, de bits (JavaScript)"
  - "opérateurs de bits, OR (opérateur)"
  - "OR (opérateur)"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# OR, op&#233;rateur d&#39;assignation de bits (|=) (JavaScript)
Effectue une opération de bits OR sur la valeur d'une variable et la valeur d'une expression, puis assigne le résultat à la variable.  
  
## Syntaxe  
  
```  
  
result |= expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 Utiliser cet opérateur revient exactement à spécifier :  
  
```javascript  
result = result | expression  
```  
  
 L'opérateur **&#124;\=** examine la représentation binaire des valeurs du *résultat* et de l'*expression*, puis effectue sur celles\-ci une opération de bits OR.  Le résultat de cette opération est le suivant :  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Lorsque l'une des expressions comporte un 1, le résultat comporte un 1.  Sinon, le résultat comporte un 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [&#124;, opérateur de bits OR](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)