---
title: "Remainder (opérateur) (JavaScript) | Documents Microsoft"
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
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>Opérateur de reste (JavaScript)
Divise la valeur d’une expression par la valeur d’un autre et retourne le reste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Arguments  
 `result`  
 Toute variable.  
  
 `number1`  
 Toute expression numérique.  
  
 `number2`  
 Toute expression numérique.  
  
## <a name="remarks"></a>Remarques  
 L’opérateur de reste divise `number1` par `number2`et retourne uniquement le reste comme `result`. Le signe de `result` est identique à celui de `number1`. La valeur de `result` est comprise entre 0 et la valeur absolue de `number2`.  
  
 Le code suivant montre comment utiliser l’opérateur de reste.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
