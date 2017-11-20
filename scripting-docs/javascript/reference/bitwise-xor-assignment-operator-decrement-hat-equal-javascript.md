---
title: "Opérateur d’assignation de bits XOR (^ =) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>XOR, opérateur d'assignation de bits (^=) (JavaScript)
Effectue une opération de bits OR exclusive sur une variable et une expression, puis assigne le résultat à la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de la  **^=**  opérateur est exactement identique à :  
  
```JavaScript  
result = result ^ expression  
```  
  
 Le  **^=**  opérateur examine la représentation binaire des valeurs de deux expressions et effectue une opération exclusive au niveau du bit sur ces derniers. Le résultat de cette opération se comporte comme suit :  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Si un seul et unique, des expressions a un 1, le résultat comporte un 1 ce chiffre. Dans le cas contraire, le résultat comporte un 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur de bits XOR (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)