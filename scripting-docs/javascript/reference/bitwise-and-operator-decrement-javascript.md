---
title: Opérateur AND au niveau du bit (&amp;) (JavaScript) | Documents Microsoft
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
- '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634239"
---
# <a name="bitwise-and-operator-amp-javascript"></a>Opérateur AND au niveau du bit (&amp;) (JavaScript)
Effectue une opération AND au niveau du bit sur deux expressions de 32 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Résultat de l'opération.  
  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le `&` effectue une opération AND au niveau du bit sur chacun des bits de deux expressions de 32 bits. Si les deux bits sont 1, le résultat est 1. Dans le cas contraire, le résultat est 0.  
  
|Bit 1|Bit 2|Valeur de liés|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Les exemples suivants montrent comment utiliser le `&` opérateur.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’assignation AND au niveau du bit (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)