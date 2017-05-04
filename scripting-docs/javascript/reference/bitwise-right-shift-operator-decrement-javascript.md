---
title: "Right Shift, op&#233;rateur de bits (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> (opérateur)"
  - ">> (opérateur), à propos de l'opérateur >>"
  - ">> (opérateur), bitsets"
  - "opérateurs de bits, opérateur de décalage vers la droite"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Right Shift, op&#233;rateur de bits (&gt;&gt;) (JavaScript)
Décale vers la droite les bits d'une expression, en conservant le signe.  
  
## Syntaxe  
  
```  
  
result = expression1 >> expression2  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression1*  
 Toute expression.  
  
 *expression2*  
 Toute expression.  
  
## Notes  
 L'opérateur \>\> décale les bits de *expression1* vers la droite du nombre de bits spécifié dans *expression2*.  Le bit de signe de *expression1* est utilisé pour remplir les chiffres à partir de la gauche.  Les chiffres qui sont décalés vers la droite sont supprimés.  Par exemple, après l'évaluation du code suivant, *temp* a une valeur de \-4 puisque \-14 \(11110010 en complément à deux binaire\) décalé vers la droite de deux bits est égal à \-4 \(11111100 en complément à deux binaire\).  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\<\< \(décalage vers la gauche\), opérateur de bits](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [\>\>\= \(décalage vers la droite\), opérateur d'assignation](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [\>\>\> \(décalage vers la droite non signé\), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)