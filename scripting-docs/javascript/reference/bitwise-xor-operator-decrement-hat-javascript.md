---
title: Opérateur de bits XOR (^) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633849"
---
# <a name="bitwise-xor-operator--javascript"></a>XOR, opérateur de bits (^) (JavaScript)
Effectue une opération de bits OR exclusive sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le  **^**  opérateur examine la représentation binaire des valeurs de deux expressions et effectue une opération exclusive au niveau du bit sur ces derniers. Le résultat de cette opération se comporte comme suit :  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Si un seul et unique, des expressions a un 1, le résultat comporte un 1 ce chiffre. Dans le cas contraire, le résultat comporte un 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’assignation de bits XOR (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)