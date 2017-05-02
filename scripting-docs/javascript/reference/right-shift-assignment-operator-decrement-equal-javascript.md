---
title: "Right Shift, op&#233;rateur d&#39;assignation (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= (opérateur) (JavaScript)"
  - "opérateurs d'assignation, JavaScript"
  - "opérateurs de décalage vers la droite (JavaScript)"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Right Shift, op&#233;rateur d&#39;assignation (&gt;&gt;=) (JavaScript)
Décale la valeur d'une variable vers la droite, du nombre de bits spécifié dans la valeur d'une expression, en conservant le signe, et assigne le résultat à la variable.  
  
## Syntaxe  
  
```  
  
result >>= expression  
```  
  
## Paramètres  
 *result*  
 Toute variable.  
  
 *expression*  
 Toute expression.  
  
## Notes  
 Utiliser l'opérateur **\>\>\=** revient exactement à spécifier :  
  
```javascript  
result = result >> expression  
```  
  
 L'opérateur **\>\>\=** décale les bits de *result* vers la droite, du nombre de bits spécifié dans le paramètre *expression*.  Le bit de signe de *result* est utilisé pour remplir les chiffres à partir de la gauche.  Les chiffres qui sont décalés vers la droite sont supprimés.  Par exemple, après l'évaluation du code ci\-dessous, *temp* a la valeur \-4 puisque 14 \(11110010 en binaire\) décalé vers la droite de deux bits est égal à \-4 \(11111100 en binaire\).  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\<\< \(décalage vers la gauche\), opérateur de bits](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [\>\> \(décalage vers la droite\), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [\>\>\> \(décalage vers la droite non signé\), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)