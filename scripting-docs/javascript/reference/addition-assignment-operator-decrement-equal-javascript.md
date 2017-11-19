---
title: "Opérateur d’assignation (+=) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Addition, opérateur d'assignation (+=) (JavaScript)
Ajoute la valeur d'une expression à la valeur d'une variable et assigne le résultat à la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 À l’aide de cet opérateur est exactement identique : `result = result + expression`.  
  
 Les types des deux expressions déterminent le comportement de la `+=` opérateur.  
  
|If|Puis|  
|--------|----------|  
|Les deux expressions sont numériques ou booléennes|Ajouter|  
|Les deux expressions sont des chaînes|Concaténer|  
|Une expression est numérique et l’autre est une chaîne|Concaténer|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’addition (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)