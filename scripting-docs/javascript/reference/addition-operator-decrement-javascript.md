---
title: "Opérateur d’addition (+) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Addition, opérateur (+) (JavaScript)
Ajoute la valeur d’une expression numérique à un autre, ou concatène deux chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Toute variable.  
  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Les types des deux expressions déterminent le comportement de la  **+**  opérateur.  
  
|If|Puis|  
|--------|----------|  
|Les deux expressions sont numériques ou booléennes|Ajouter|  
|Les deux expressions sont des chaînes|Concaténer|  
|Une expression est numérique et l’autre est une chaîne|Concaténer|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur d’assignation (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)