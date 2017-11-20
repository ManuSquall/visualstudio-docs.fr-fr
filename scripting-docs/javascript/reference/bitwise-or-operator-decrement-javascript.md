---
title: "Au niveau du bit OR (opérateur) (|) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-operator--javascript"></a>OR, opérateur de bits (|) (JavaScript)
Effectue une opération de bits OR sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le **&#124;** opérateur examine la représentation binaire des valeurs de deux expressions et effectue une opération OR au niveau du bit sur ces derniers. Le résultat de cette opération se comporte comme suit :  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Chaque fois qu’une des expressions a un 1, le résultat comporte un 1. Dans le cas contraire, le résultat comporte un 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit ou opérateur d’assignation (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)