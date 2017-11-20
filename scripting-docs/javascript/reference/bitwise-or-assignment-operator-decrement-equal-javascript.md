---
title: "Au niveau du bit ou opérateur d’assignation (| =) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>OR, opérateur d'assignation de bits (|=) (JavaScript)
Effectue une opération de bits OR sur la valeur d'une variable et la valeur d'une expression, puis assigne le résultat à la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de cet opérateur est exactement identique à :  
  
```JavaScript  
result = result | expression  
```  
  
 Le **&#124; =** opérateur examine la représentation binaire des valeurs de *résultat* et *expression* et effectue une opération OR au niveau du bit sur ces derniers. Le résultat de cette opération se comporte comme suit :  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Chaque fois qu’une des expressions a un 1, le résultat comporte un 1 dans ce chiffre. Dans le cas contraire, le résultat comporte un 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit OR (opérateur &#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)