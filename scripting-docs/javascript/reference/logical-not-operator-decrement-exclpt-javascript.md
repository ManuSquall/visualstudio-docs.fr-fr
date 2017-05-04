---
title: "! (NOT logique), op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! d'opérateur"
  - "! d'opérateur, à propos de l'opérateur !"
  - "NOT logique (opérateur)"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# ! (NOT logique), op&#233;rateur (JavaScript)
Effectue une négation logique sur une expression.  
  
## Syntaxe  
  
```  
  
result = !expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 Le tableau suivant illustre comment le *résultat* est déterminé.  
  
|Si l'argument `expression` a la valeur :|L'argument `result` prend la valeur|  
|----------------------------------------------|-----------------------------------------|  
|True|False|  
|False|True|  
  
 Tous les opérateurs unaires, tels que l'opérateur **\!**, évaluent les expressions de la façon suivante :  
  
-   Si l'opérateur est appliqué à des expressions undefined ou `null`, une erreur d'exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Dans la mesure du possible, les chaînes sont converties en nombres.  Sinon, une erreur d'exécution est générée.  
  
-   Les valeurs booléennes sont traitées comme des nombres \(0 pour la valeur False, 1 pour la valeur True\).  
  
 L'opérateur est appliqué au nombre résultant.  
  
 Pour l'opérateur **\!**, si l'argument *expression* est différent de zéro, l'argument *result* est égal à zéro.  Si l'argument *expression* a la valeur zéro, l'argument *result* a la valeur 1.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [~, opérateur de bits NOT](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)