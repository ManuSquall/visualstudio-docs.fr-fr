---
title: "Op&#233;rateurs de comparaison (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs de comparaison, script"
  - "supérieur à (opérateur)"
  - "opérateurs de comparaison"
  - "supérieur ou égal à (opérateur)"
  - "inégalité (opérateur)"
  - "identité (opérateur)"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Op&#233;rateurs de comparaison (JavaScript)
Retourne une valeur booléenne indiquant le résultat de la comparaison.  
  
## Syntaxe  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## Paramètres  
 `expression1`  
 Toute expression.  
  
 `comparisonoperator`  
 Tout opérateur de comparaison.  
  
 `expression2`  
 Toute expression.  
  
## Notes  
 Pour comparer des chaînes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur des caractères Unicode de l'expression chaîne.  
  
 La section suivante décrit le comportement des différents groupes d'opérateurs en fonction des types et des valeurs des arguments `expression1` et `expression2` :  
  
 Opérateurs relationnels : `<`, `>`, `<=`, `>=`  
  
-   Ces opérateurs tentent de convertir `expression1` et `expression2` en nombres.  
  
-   Si les deux expressions sont des chaînes, ces opérateurs effectuent une comparaison de chaînes.  
  
-   Si l'une des deux expressions a la valeur `NaN`, ces opérateurs retournent la valeur `false`.  
  
-   Un zéro négatif égale un zéro positif.  
  
-   L'infini négatif est plus petit que n'importe quelle autre valeur y compris lui\-même.  
  
-   L'infini positif est plus grand que n'importe quelle autre valeur y compris lui\-même.  
  
 Opérateurs d'égalité : `==`, `!=`  
  
-   Si les types des deux expressions sont différents, ces opérateurs tentent de les convertir en chaîne, en nombre ou en valeur booléenne.  
  
-   `NaN` est différent de n'importe quelle autre valeur y compris lui\-même.  
  
-   Un zéro négatif égale un zéro positif.  
  
-   `null` est égal à `null` et à `undefined`.  
  
-   Des valeurs sont considérées égales si elles constituent des chaînes identiques, des nombres numériquement équivalents, le même objet, des valeurs booléennes identiques ou, lorsqu'elles appartiennent à des types différents, si elles peuvent être converties de manière à satisfaire une de ces conditions.  
  
-   Toute autre comparaison doit être considérée comme inégale.  
  
 Opérateurs d'identité : `===`, `!==`  
  
 Ces opérateurs se comportent de la même manière que les opérateurs d'égalité, à ceci près qu'aucune conversion de type n'est effectuée.  Si les types des deux expressions ne sont pas identiques, ces expressions retournent toujours `false`.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)