---
title: "NOT, op&#233;rateur de bits (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs de bits, NOT (opérateur)"
  - "NOT (opérateur)"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# NOT, op&#233;rateur de bits (~) (JavaScript)
Effectue une opération de bits NOT \(négation\) sur une expression.  
  
## Syntaxe  
  
```  
  
result = ~ expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 Tous les opérateurs unaires, tels que l'opérateur `~`, évaluent les expressions de la façon suivante :  
  
-   Si l'opérateur est appliqué à des expressions undefined ou `null`, une erreur d'exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Dans la mesure du possible, les chaînes sont converties en nombres.  Sinon, une erreur d'exécution est générée.  
  
-   Les valeurs booléennes sont traitées comme des nombres \(0 pour la valeur False, 1 pour la valeur True\).  
  
 L'opérateur est appliqué au nombre résultant.  
  
 L'opérateur `~` examine la représentation binaire des valeurs de l'expression, puis effectue sur celles\-ci une opération de bits de négation.  
  
 Tout chiffre 1 dans l'expression devient un 0 dans le résultat.  Tout chiffre 0 dans l'expression devient un 1 dans le résultat.  
  
 L'exemple suivant illustre l'utilisation de l'opérateur de bits NOT \(~\).  
  
```  
var temp = ~5;  
```  
  
 La valeur obtenue est \-6, comme le montre le tableau suivant.  
  
|Expression|Valeur binaire \(complément de deux\)|Valeur décimale|  
|----------------|-------------------------------------------|---------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\! \(NOT logique\), opérateur](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)