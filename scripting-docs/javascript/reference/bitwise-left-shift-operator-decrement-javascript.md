---
title: "Left Shift, op&#233;rateur de bits (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< (opérateur)"
  - "<< (opérateur), à propos de l'opérateur <<"
  - "opérateurs de bits, opérateur de décalage"
  - "opérateurs de décalage vers la gauche"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Left Shift, op&#233;rateur de bits (&lt;&lt;) (JavaScript)
Décale les bits d'une expression vers la gauche.  
  
## Syntaxe  
  
```  
  
result = expression1 << expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 L'opérateur **\<\<** décale les bits d'*expression1* vers la gauche du nombre de bits spécifié dans *expression2*.  Par exemple :  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 La variable *temp* a la valeur 56, étant donné que 14 \(00001110 en binaire\) est égal à 56 \(00111000 en binaire\) après un décalage de deux bits vers la gauche.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\<\<\= \(décalage vers la gauche\), opérateur d'assignation](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [\>\> \(décalage vers la droite\), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [\>\>\> \(décalage vers la droite non signé\), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)