---
title: "Opérateur d’assignation AND au niveau du bit (&amp;=) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Opérateur d’assignation AND au niveau du bit (&amp;=) (JavaScript)
Définit le résultat d’une opération AND au niveau du bit sur la valeur d’une variable et la valeur d’une expression. La variable et l’expression sont traités en tant qu’entiers 32 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de cet opérateur est identique à :  
  
```JavaScript  
result = result & expression  
```  
  
 Le [et opérateur (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) examine la représentation binaire des valeurs de `result` et `expression` et effectue une opération AND au niveau du bit sur ces derniers. La sortie de cette opération se comporte comme suit :  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Lorsque les que deux expressions ont un 1 dans un chiffre, le résultat comporte un 1 dans ce chiffre. Dans le cas contraire, le résultat comporte un 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur de bits AND (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)