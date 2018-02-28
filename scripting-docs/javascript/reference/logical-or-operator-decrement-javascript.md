---
title: "Logique OR (opérateur) (|) (JavaScript) | Documents Microsoft"
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
- '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>OR, opérateur logique (||) (JavaScript)
Effectue une disjonction logique sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *Expression2*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Si un ou les deux expressions ont **True**, *résultat* est **True**. Le tableau suivant illustre comment *résultat* est déterminé :  
  
|Si `expression1` est|Et `expression2` est|Le `result` est|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise les règles suivantes pour la conversion de valeurs non booléennes en valeurs booléennes :  
  
-   Tous les objets sont considérés comme true.  
  
-   Chaînes sont considérées comme false si et seulement si elles sont vides.  
  
-   `null`et non définies sont considérées comme false.  
  
-   Les numéros sont false si et seulement si, elles sont 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)