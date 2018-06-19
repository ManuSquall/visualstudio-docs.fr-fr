---
title: Opérateur d’assignation avec le bouton droit (&gt;&gt;=) (JavaScript) | Documents Microsoft
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
- '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640439"
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Opérateur d’assignation avec le bouton droit (&gt;&gt;=) (JavaScript)
Décale la valeur d'une variable vers la droite, du nombre de bits spécifié dans la valeur d'une expression, en conservant le signe, et assigne le résultat à la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de la  **>>=**  opérateur est exactement identique à :  
  
```JavaScript  
result = result >> expression  
```  
  
 Le  **>>=**  opérateur décale les bits de *résultat* à droite en fonction du nombre de bits spécifié dans *expression*. Le signe de bits de *résultat* est utilisé pour remplir les chiffres à gauche. Chiffres décalée vers la droite sont ignorés. Par exemple, une fois que le code suivant est évalué, *temp* a une valeur de -4 : 14 (11110010 en binaire) décalé vers la droite de deux bits égal à -4 (11111100 en binaire).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite au niveau du bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Opérateur de décalage vers la droite non signé (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)