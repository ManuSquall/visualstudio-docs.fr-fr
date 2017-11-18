---
title: "Opérateurs de comparaison (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Opérateurs de comparaison (JavaScript)
Retourne une valeur booléenne indiquant le résultat de la comparaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 `expression1`  
 Toute expression.  
  
 `comparisonoperator`  
 Tout opérateur de comparaison.  
  
 `expression2`  
 Toute expression.  
  
## <a name="remarks"></a>Remarques  
 Lors de la comparaison de chaînes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur de caractère Unicode de l’expression de chaîne.  
  
 La section suivante décrit comment les différents groupes d’opérateurs se comportent selon les types et les valeurs de `expression1` et `expression2`:  
  
 Opérateurs relationnels : `<`, `>`, `<=`,`>=`  
  
-   Essayez de convertir les deux `expression1` et `expression2` en nombres.  
  
-   Si les deux expressions sont des chaînes, effectuer une comparaison de chaînes.  
  
-   Si des expressions sont `NaN`, return `false`.  
  
-   Un zéro négatif est égal à zéro positif.  
  
-   L’infini négatif est inférieur à y compris lui-même.  
  
-   L’infini positif est supérieur à y compris lui-même.  
  
 Opérateurs d’égalité : `==`,`!=`  
  
-   Si les types des deux expressions sont différentes, essayez de les convertir en une chaîne, un nombre ou une valeur booléenne.  
  
-   `NaN`n’est pas égal à quoi que ce soit, y compris lui-même.  
  
-   Un zéro négatif est égal à zéro positif.  
  
-   `null`est égal à deux `null` et `undefined`.  
  
-   Les valeurs sont considérées comme égales si elles sont des chaînes identiques, nombres numériquement équivalents, le même objet, les valeurs booléennes identiques, ou (si des types différents) elles pouvant être convertis en une de ces situations.  
  
-   Toutes les autres comparaisons sont considéré comme inégaux.  
  
 Opérateurs d’identité : `===`,`!==`  
  
 Ces opérateurs comportent comme les opérateurs d’égalité, sauf qu’aucune conversion n’est effectuée. Si les types des deux expressions ne sont pas identiques, ces expressions retournent toujours `false`.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)