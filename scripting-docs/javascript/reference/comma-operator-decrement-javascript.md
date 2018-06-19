---
title: Opérateur virgule (,) (JavaScript) | Documents Microsoft
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
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634179"
---
# <a name="comma-operator--javascript"></a>comma, opérateur (,) (JavaScript)
Entraîne l'exécution séquentielle de deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le `,` opérateur entraîne les expressions à exécuter dans l’ordre de gauche à droite. Une utilisation courante pour le `,` opérateur est dans l’expression d’incrément d’une `for` boucle. Exemple :  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 La `for` instruction autorise uniquement une seule expression à exécuter à la fin de chaque boucle. Le `,` opérateur permet plusieurs expressions est traitée comme une expression unique, donc les deux variables peuvent être incrémentés.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)