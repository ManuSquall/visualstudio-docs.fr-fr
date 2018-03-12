---
title: "Opérateur de soustraction (-) (JavaScript) | Documents Microsoft"
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
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Subtraction, opérateur (-) (JavaScript)
Soustrait la valeur d’une expression d’une autre, ou fournit une négation unaire d’une expression unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Paramètres  
 *résultat*  
 Toute variable numérique.  
  
 `number`  
 Toute expression numérique.  
  
 `number1`  
 Toute expression numérique.  
  
 `number2`  
 Toute expression numérique.  
  
## <a name="remarks"></a>Remarques  
 Dans la syntaxe 1, le  **-**  opérateur est l’opérateur de soustraction arithmétique utilisé pour rechercher la différence entre deux nombres. Dans la syntaxe 2, le  **-**  opérateur est utilisé comme opérateur de négation unaire pour indiquer la valeur négative d’une expression.  
  
 Pour la syntaxe 2, comme pour tous les opérateurs unaires, les expressions sont évaluées de la comme suit :  
  
-   Si appliqué non définie ou `null` expressions, une erreur d’exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Si possible, les chaînes sont converties en nombres. Si ce n’est pas le cas, une erreur d’exécution est générée.  
  
-   Valeurs booléennes sont traitées comme des nombres (0 pour false, 1 si la valeur est true).  
  
 L’opérateur est appliqué au résultat. Dans la syntaxe 2, si le résultat est différent de zéro, *résultat* est égal au résultat avec son signe inversé. Si le nombre résultant est égal à zéro, *résultat* est égal à zéro.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’assignation de soustraction (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)