---
title: "Right Shift, op&#233;rateur d&#39;assignation non sign&#233; (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= (opérateur)"
  - "opérateurs d'assignation, JavaScript"
  - ">>>= décalage vers la droite non signé (>>>=) (opérateur d'assignation)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Right Shift, op&#233;rateur d&#39;assignation non sign&#233; (&gt;&gt;&gt;=) (JavaScript)
Décale la valeur d'une variable vers la droite, du nombre de bits spécifié dans la valeur d'une expression, sans conserver le signe, et assigne le résultat à la variable.  
  
## Syntaxe  
  
```  
  
result >>>= expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 L'utilisation de l'opérateur \>\>\>\= revient exactement à faire ce qui suit :  
  
```javascript  
result = result >>> expression  
```  
  
 L'opérateur **\>\>\>\=** décale les bits de *result* vers la droite, du nombre de bits spécifié dans le paramètre *expression*.  Des zéros sont remplis en partant de la gauche.  Les chiffres qui sont décalés vers la droite sont supprimés.  Par exemple :  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variable *temp* a la valeur initiale \-14 \(11111111 11111111 11111111 11110010 dans un binaire en complément à deux\).  Lorsqu'il est déplacé de deux bits vers la droite, la valeur est égale à 1 073 741 820 \(00111111 11111111 11111111 11111100 en binaire\).  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\>\>\> \(décalage vers la droite non signé\), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [\<\< \(décalage vers la gauche\), opérateur de bits](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [\>\> \(décalage vers la droite\), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)