---
title: "OR, op&#233;rateur logique (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| (opérateur)"
  - "opérateur logique OR"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# OR, op&#233;rateur logique (||) (JavaScript)
Effectue une disjonction logique sur deux expressions.  
  
## Syntaxe  
  
```  
  
result = expression1 || expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 Si l'une des expressions, ou les deux, ont la valeur **True**, le *résultat* a la valeur **True**.  Le tableau suivant illustre comment le *résultat* est déterminé :  
  
|Si `expression1` a la valeur|Et si `expression2` a la valeur|`result` a la valeur|  
|----------------------------------|-------------------------------------|--------------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise les règles de conversion de valeurs non booléennes en valeurs booléennes présentées ci\-dessous :  
  
-   Tous les objets sont considérés vrais \(true\).  
  
-   Les chaînes sont considérées fausses \(false\) si, et seulement si, elles sont vides.  
  
-   Les valeurs `null` et undefined sont considérées fausses \(false\).  
  
-   Les nombres sont considérés faux \(false\) si et seulement s'ils ont pour valeur 0.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)