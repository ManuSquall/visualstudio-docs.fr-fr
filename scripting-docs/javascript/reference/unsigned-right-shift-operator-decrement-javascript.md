---
title: "Right Shift, op&#233;rateur non sign&#233; (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> (opérateur)"
  - "décalage vers la droite non signé (>>>) (opérateur)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Right Shift, op&#233;rateur non sign&#233; (&gt;&gt;&gt;) (JavaScript)
Décale vers la droite les bits d'une expression, sans conserver le signe.  
  
## Syntaxe  
  
```  
  
result = expression1 >>> expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 L'opérateur **\>\>\>** décale les bits d'*expression1* vers la droite du nombre de bits spécifié dans *expression2*.  Des zéros sont remplis en partant de la gauche.  Les chiffres qui sont décalés vers la droite sont supprimés.  Par exemple :  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 La variable *temp* possède une valeur initiale de \-14 \(11111111 11111111 11111111 11110010 dans un binaire de complément à deux\).  Lorsqu'elle est déplacée de deux bits vers la droite, la valeur est égale à 1 073 741 820 \(soit 00111111 11111111 11111111 11111100 en binaire\).  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\>\>\>\= \(décalage vers la droite non signé\), opérateur d'assignation](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [\<\< \(décalage vers la gauche\), opérateur de bits](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [\>\> \(décalage vers la droite\), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)