---
title: Au niveau du bit NOT (opérateur) (~) (JavaScript) | Documents Microsoft
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
- "~"
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634259"
---
# <a name="bitwise-not-operator--javascript"></a>NOT, opérateur de bits (~) (JavaScript)
Effectue une opération de bits NOT (négation) sur une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Tous les opérateurs unaires, telles que le `~` évaluent les expressions comme suit :  
  
-   Si appliqué non définie ou `null` expressions, une erreur d’exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Si possible, les chaînes sont converties en nombres. Si ce n’est pas le cas, une erreur d’exécution est générée.  
  
-   Valeurs booléennes sont traitées comme des nombres (0 pour false, 1 si la valeur est true).  
  
 L’opérateur est appliqué au résultat.  
  
 Le `~` opérateur examine la représentation binaire des valeurs de l’expression et effectue une opération de négation au niveau du bit sur celui-ci.  
  
 Tout chiffre 1 dans l’expression devient un 0 dans le résultat. Tout chiffre 0 dans l’expression devient un 1 dans le résultat.  
  
 L’exemple suivant illustre l’utilisation de l’opérateur de bits NOT (opérateur) (~).  
  
```  
var temp = ~5;  
```  
  
 La valeur résultante est -6, comme indiqué dans le tableau suivant.  
  
|Expression|Valeur binaire (du complément à deux)|Valeur décimale|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Logique l’opérateur NOT ( !)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)