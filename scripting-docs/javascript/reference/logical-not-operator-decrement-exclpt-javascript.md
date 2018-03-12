---
title: "Logique l’opérateur NOT ( !) (JavaScript) | Documents Microsoft"
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>! (NOT logique), opérateur (JavaScript)
Effectue une négation logique sur une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant illustre comment *résultat* est déterminée.  
  
|Si `expression` est|Puis `result` est|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 Tous les opérateurs unaires, telles que le **!** évaluent les expressions comme suit :  
  
-   Si appliqué non définie ou `null` expressions, une erreur d’exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Si possible, les chaînes sont converties en nombres. Si ce n’est pas le cas, une erreur d’exécution est générée.  
  
-   Valeurs booléennes sont traitées comme des nombres (0 pour false, 1 si la valeur est true).  
  
 L’opérateur est appliqué au résultat.  
  
 Pour le **!** opérateur, si *expression* est différent de zéro, *résultat* est égal à zéro. Si *expression* est égal à zéro, *résultat* est 1.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Au niveau du bit NOT (opérateur) (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)