---
title: "Op&#233;rateur d’assignation de d&#233;calage vers la gauche (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= (opérateur) (JavaScript)"
  - "décalage vers la gauche (<<=) (opérateur d’assignation) (JavaScript)"
  - "opérateurs de décalage vers la gauche (JavaScript)"
  - "opérateurs d’assignation, JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Op&#233;rateur d’assignation de d&#233;calage vers la gauche (&lt;&lt;=) (JavaScript)
Déplace le nombre de bits spécifié vers la gauche et assigne le résultat au `result`.  Les bits libérés par l'opération sont remplis avec 0.  
  
## Syntaxe  
  
```  
  
result <<= expression  
```  
  
## Paramètres  
 `result`  
 Toute variable.  
  
 `expression`  
 Déplacement en nombre de bits.  
  
## Notes  
 Utiliser l'opérateur `<<=` revient à spécifier `result = result << expression`.  
  
 L'exemple suivant illustre l'utilisation de l'opérateur `<<=`.  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [\<\< \(décalage vers la gauche\), opérateur de bits](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [\>\> \(décalage vers la droite\), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [\>\>\> \(décalage vers la droite non signé\), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)