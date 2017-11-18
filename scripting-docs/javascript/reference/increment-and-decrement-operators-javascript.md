---
title: "++ (Incrémentation) et les opérateurs de décrémentation (--) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>incrémentation (++) et décrémentation (--), opérateurs (JavaScript)
Les incréments d’opérateur d’incrémentation et de l’opérateur de décrémentation décrémente la valeur d’une variable d’une unité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `variable`  
 Toute variable.  
  
## <a name="remarks"></a>Remarques  
 Si l’opérateur apparaît avant la variable, la valeur est modifiée avant que l’expression est évaluée. Si l’opérateur apparaît après la variable, la valeur est modifiée une fois que l’expression est évaluée.  En d’autres termes, étant donné `j = ++k;`, la valeur de `j` est la valeur d’origine de `k` plus un ; donné `j = k++;`, la valeur de `j` est la valeur d’origine `k`, qui est incrémenté une fois que sa valeur est assignée à `j`.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)