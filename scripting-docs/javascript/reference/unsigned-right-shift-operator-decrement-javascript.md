---
title: "Opérateur de décalage vers la droite non signé (&gt;&gt;&gt;) (JavaScript) | Documents Microsoft"
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
- '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Opérateur de décalage vers la droite non signé (&gt;&gt;&gt;) (JavaScript)
Décale vers la droite les bits d’une expression, sans conserver le signe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le  **>>>**  opérateur décale les bits de *expression1* à droite en fonction du nombre de bits spécifié dans *expression2*. Des zéros sont remplis à partir de la gauche. Chiffres décalée vers la droite sont ignorés. Exemple :  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 La variable *temp* possède une valeur initiale -14 (11111111 11111111 11111111 11110010 dans un binaire de complément à deux). Lorsqu’elle est décalée de deux bits vers la droite, la valeur est égale à 1073741820 (00111111 11111111 11111111 11111100 en binaire).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Non signé opérateur d’assignation de décalage vers la droite (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite au niveau du bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)