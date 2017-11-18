---
title: "Opérateur d’assignation de reste (&lt;&lt;=) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Opérateur d’assignation de reste (&lt;&lt;=) (JavaScript)
Déplace le nombre spécifié de bits vers la gauche et assigne le résultat à `result`. Les bits libérées par l’opération sont remplis par 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Le nombre de bits à déplacer.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de la `<<=` opérateur équivaut à spécifier`result = result << expression`  
  
 L'exemple suivant illustre l'utilisation de l'opérateur `<<=`.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite au niveau du bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite non signé (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)