---
title: "Opérateur de décalage vers la droite au niveau du bit (&gt;&gt;) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Opérateur de décalage vers la droite au niveau du bit (&gt;&gt;) (JavaScript)
Décale vers la droite les bits d’une expression, en conservant le signe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le >> opérateur décale les bits de *expression1* à droite en fonction du nombre de bits spécifié dans *expression2*. Le signe de bits de *expression1* est utilisé pour remplir les chiffres à gauche. Chiffres décalée vers la droite sont ignorés. Par exemple, une fois que le code suivant est évalué, *temp* a une valeur de -4 :-14 (11110010 dans deux complément binaires) décalé vers la droite de deux bits égal à -4 (11111100 dans deux complément binaires).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Opérateur d’assignation avec le bouton droit (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Opérateur de décalage vers la droite non signé (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)