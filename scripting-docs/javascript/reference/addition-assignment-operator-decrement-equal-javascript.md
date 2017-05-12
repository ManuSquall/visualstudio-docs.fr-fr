---
title: "Addition, op&#233;rateur d&#39;assignation (+=) (JavaScript) | Microsoft Docs"
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
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "+= (addition) (opérateur d'assignation)"
  - "+= (opérateur)"
  - "opérateurs d’assignation, JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Addition, op&#233;rateur d&#39;assignation (+=) (JavaScript)
Ajoute la valeur d'une expression à la valeur d'une variable et assigne le résultat à la variable.  
  
## Syntaxe  
  
```  
  
result += expression   
```  
  
## Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Toute expression.  
  
## Notes  
 Utiliser cet opérateur revient exactement à spécifier : `result = result + expression`.  
  
 Les types des deux expressions déterminent le comportement de l'opérateur `+=`.  
  
|Si|Alors|  
|--------|-----------|  
|Les deux expressions sont numériques ou boolean|Ajouter|  
|Les deux expressions sont des chaînes|Concaténer|  
|Une expression est numérique et l'autre est une chaîne|Concaténer|  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Opérateur d'addition \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)