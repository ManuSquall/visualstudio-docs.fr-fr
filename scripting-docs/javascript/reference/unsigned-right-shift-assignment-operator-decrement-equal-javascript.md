---
title: Non signé opérateur d’assignation de décalage vers la droite (&gt;&gt;&gt;=) (JavaScript) | Documents Microsoft
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
- '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641389"
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Non signé opérateur d’assignation de décalage vers la droite (&gt;&gt;&gt;=) (JavaScript)
Décale la valeur d'une variable vers la droite, du nombre de bits spécifié dans la valeur d'une expression, sans conserver le signe, et assigne le résultat à la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de la >>> = opérateur est exactement le même que la manière suivante :  
  
```JavaScript  
result = result >>> expression  
```  
  
 Le  **>>>=**  opérateur décale les bits de *résultat* à droite en fonction du nombre de bits spécifié dans *expression*. Des zéros sont remplis à partir de la gauche. Chiffres décalée vers la droite sont ignorés. Exemple :  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variable *temp* possède une valeur initiale de -14 (11111111 11111111 11111111 11110010 dans un binaire de complément à deux). Lorsque décalée vers la droite de deux bits, la valeur est égale à 1073741820 (00111111 11111111 11111111 11111100 en binaire).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur de décalage vers la droite non signé (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite au niveau du bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)