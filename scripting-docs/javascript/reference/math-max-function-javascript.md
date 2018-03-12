---
title: Math.max, fonction (JavaScript) | Documents Microsoft
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
- max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Math.max, fonction (JavaScript)
Retourne le plus grand d’un ensemble d’expressions numériques fournies.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif `number1, number2, ..., numberN` arguments sont des expressions numériques à évaluer.  
  
 Si aucun argument n’est fourni, la valeur de retour est égale à [Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Si un argument est `NaN`, la valeur de retour est également `NaN`.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment obtenir le plus grand de deux expressions.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.min](../../javascript/reference/math-min-function-javascript.md)