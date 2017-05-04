---
title: "Subtraction, op&#233;rateur (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- (opérateur)"
  - "- (opérateur), à propos de l'opérateur -"
  - "opérateurs arithmétiques, soustraction"
  - "négation (opérateur)"
  - "opérateurs, soustraction"
  - "soustraction (opérateur), syntaxe"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Subtraction, op&#233;rateur (-) (JavaScript)
Soustrait la valeur d'une expression d'une autre valeur et fournit une négation unaire d'une expression unique.  
  
## Syntaxe  
  
```  
  
result = number1 - number2;  
  
```  
  
## Paramètres  
 *result*  
 Toute variable numérique.  
  
 `number`  
 Toute expression numérique.  
  
 `number1`  
 Toute expression numérique.  
  
 `number2`  
 Toute expression numérique.  
  
## Notes  
 Dans la syntaxe 1, l'opérateur **–** est l'opérateur de soustraction arithmétique utilisé pour trouver la différence entre deux nombres.  Dans la syntaxe 2, l'opérateur **–** est utilisé comme opérateur de négation unaire pour indiquer la valeur négative d'une expression.  
  
 Pour la syntaxe 2, comme pour tous les opérateurs unaires, les expressions sont évaluées de la façon suivante :  
  
-   Si l'opérateur est appliqué à des expressions undefined ou `null`, une erreur d'exécution est générée.  
  
-   Les objets sont convertis en chaînes.  
  
-   Dans la mesure du possible, les chaînes sont converties en nombres.  Sinon, une erreur d'exécution est générée.  
  
-   Les valeurs booléennes sont traitées comme des nombres \(0 pour la valeur False, 1 pour la valeur True\).  
  
 L'opérateur est appliqué au nombre résultant.  Dans la syntaxe 2, si le nombre résultant est différent de zéro, le *result* est égal au nombre résultant mais avec son signe inversé.  Si le nombre résultant a la valeur zéro, le *result* a la valeur zéro.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\-\= \(soustraction\), opérateur d'assignation](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)