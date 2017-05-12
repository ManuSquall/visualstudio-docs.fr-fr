---
title: "incr&#233;mentation (++) et d&#233;cr&#233;mentation (--), op&#233;rateurs (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "opérateurs d’incrémentation, syntaxe"
  - "++ (opérateur)"
  - "++ (opérateur), à propos de l’opérateur ++"
  - "opérateurs de décrémentation, syntaxe"
  - "-- (opérateur)"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# incr&#233;mentation (++) et d&#233;cr&#233;mentation (--), op&#233;rateurs (JavaScript)
L'opérateur d'incrémentation incrémente d'une unité la valeur d'une variable ; l'opérateur de décrémentation décrémente d'une unité la valeur d'une variable.  
  
## Syntaxe  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## Paramètres  
 `result`  
 Toute variable.  
  
 `variable`  
 Toute variable.  
  
## Notes  
 Si l'opérateur apparaît avant la variable, la valeur est modifiée avant l'évaluation de l'expression.  Si l'opérateur apparaît après la variable, la valeur est modifiée après l'évaluation de l'expression.  En d'autres termes, étant donné `j = ++k;`, la valeur de `j` est la valeur d'origine de `k` plus un ; étant donné `j = k++;`, la valeur de `j` est la valeur d'origine de `k`, qui est incrémenté lorsque sa valeur est assignée à `j`.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)