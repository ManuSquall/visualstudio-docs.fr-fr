---
title: "Addition, op&#233;rateur (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs arithmétiques, addition"
  - "chaînes (Visual Studio), concaténer"
  - "opérateurs de concaténation, différences par rapport à l’opérateur d’addition"
  - "opérateur d'addition"
  - "+ (opérateur)"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Addition, op&#233;rateur (+) (JavaScript)
Additionne la valeur d'une expression numérique avec une autre valeur ou concatène deux chaînes.  
  
## Syntaxe  
  
```  
  
result = expression1 + expression2  
```  
  
## Paramètres  
 `result`  
 Toute variable.  
  
 `expression1`  
 Toute expression.  
  
 `expression2`  
 Toute expression.  
  
## Notes  
 Les types des deux expressions déterminent le comportement de l'opérateur **\+**.  
  
|Si|Alors|  
|--------|-----------|  
|Les deux expressions sont numériques ou boolean|Ajouter|  
|Les deux expressions sont des chaînes|Concaténer|  
|Une expression est numérique et l'autre est une chaîne|Concaténer|  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Opérateur d'assignation d'addition \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)