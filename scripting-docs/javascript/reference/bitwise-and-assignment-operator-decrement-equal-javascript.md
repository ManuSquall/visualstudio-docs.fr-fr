---
title: "AND, op&#233;rateur d&#39;assignation de bits (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= (opérateur)"
  - "opérateurs d’assignation, au niveau du bit (JavaScript)"
  - "AND (opérateur)"
  - "opérateurs de bits, opérateur AND"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# AND, op&#233;rateur d&#39;assignation de bits (&amp;=) (JavaScript)
Définit le résultat de l'opération de bits AND sur la valeur d'une variable et la valeur d'une expression.  La variable et l'expression sont traitées comme un entier 32 bits.  
  
## Syntaxe  
  
```  
  
result &= expression  
```  
  
## Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Toute expression.  
  
## Notes  
 Utiliser cet opérateur revient à spécifier :  
  
```javascript  
result = result & expression  
```  
  
 L'opérateur [&, opérateur de bits AND](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) examine la représentation binaire des valeurs `result` et `expression` et effectue une opération de bits AND sur celles\-ci.  Le résultat de cette opération est le suivant :  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 Lorsque deux expressions possèdent un 1, le résultat comporte un 1.  Sinon, le résultat comporte un 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [&, opérateur de bits AND](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)