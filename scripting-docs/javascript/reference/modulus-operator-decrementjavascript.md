---
title: "Modulus, op&#233;rateur (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "Modulus (opérateur), JavaScript"
  - "% (opérateur) (JavaScript)"
  - "Modulo (fonction) (JavaScript)"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modulus, op&#233;rateur (JavaScript)
Divise la valeur d'une expression par la valeur d'une autre et retourne le reste.  
  
## Syntaxe  
  
```  
  
result = number1 % number2  
```  
  
## Arguments  
 `result`  
 Toute variable.  
  
 `number1`  
 Toute expression numérique.  
  
 `number2`  
 Toute expression numérique.  
  
## Notes  
 L'opérateur modulo, ou reste, divise `number1` par `number2` et retourne uniquement le reste en tant que `result`.  Le signe de `result` est le même que celui de `number1`.  La valeur de `result` est comprise entre 0 et la valeur absolue de `number2`.  
  
 Le code suivant illustre l'utilisation de l'opérateur modulo.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)