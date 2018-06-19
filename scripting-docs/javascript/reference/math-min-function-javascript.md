---
title: Math.min, fonction (JavaScript) | Documents Microsoft
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
- min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639079"
---
# <a name="mathmin-function-javascript"></a>Math.min, fonction (JavaScript)
Retourne le plus petit d’un ensemble d’expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif `number1, number2, ..., numberN` arguments sont des expressions numériques à évaluer.  
  
 Si aucun argument n’est fourni, la valeur de retour est égale à [Number.POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Si un argument est `NaN`, la valeur de retour est également `NaN`.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment obtenir le plus petit de deux expressions.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.max](../../javascript/reference/math-max-function-javascript.md)