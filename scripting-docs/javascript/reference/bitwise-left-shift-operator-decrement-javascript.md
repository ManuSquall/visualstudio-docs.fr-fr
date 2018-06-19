---
title: Au niveau du bit opérateur Left Shift (&lt;&lt;) (JavaScript) | Documents Microsoft
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
- <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634209"
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Au niveau du bit opérateur Left Shift (&lt;&lt;) (JavaScript)
Décale vers la gauche les bits d’une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le  **<<**  opérateur décale les bits de *expression1* gauche par le nombre de bits spécifié dans *expression2*. Exemple :  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 La variable *temp* a la valeur 56 puisque 14 (00001110 en binaire) décalé vers la gauche deux bits est égal à 56 (00111000 en binaire).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’assignation de gauche (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Opérateur de décalage vers la droite au niveau du bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite non signé (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)