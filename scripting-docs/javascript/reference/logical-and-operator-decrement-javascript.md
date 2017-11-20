---
title: "Opérateur AND logique (&amp;&amp;) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>Opérateur AND logique (&amp;&amp;) (JavaScript)
Effectue une conjonction logique sur deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Si `expression1` a la valeur `false`, `result` est `expression1`. Sinon, `result` est `expression2`. Par conséquent, l'opération retourne `true` si les deux opérandes sont vrais ; sinon, elle retourne `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise les règles suivantes pour la conversion de valeurs non booléennes en valeurs booléennes :  
  
-   Tous les objets sont considérés comme `true`.  
  
-   Les chaînes sont considérées comme `false` si elles sont vides.  
  
-   `null` et `undefined` sont considérés comme `false`.  
  
-   Un nombre est `false` s'il est égal à zéro.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)