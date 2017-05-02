---
title: "typeof, op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "TypeOf (opérateur)"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof, op&#233;rateur (JavaScript)
Retourne une chaîne qui identifie le type de données d'une expression.  
  
## Syntaxe  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## Notes  
 L'argument *expression* est une expression pour laquelle les informations de type sont recherchées.  
  
 L'opérateur `typeof` retourne les informations de type sous forme d'une chaîne de caractères.  Six valeurs différentes peuvent être retournées par l'opérateur `typeof` : « number », « string », « boolean », « object », « function » et « undefined ».  
  
 Les parenthèses sont facultatives dans la syntaxe de l'opérateur `typeof`.  
  
## Exemple  
 L'exemple suivant présente les tests du type de données des variables.  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## Exemple  
 L'exemple suivant présente les tests d'un type de données `undefined` pour les variables déclarées et non déclarées.  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Array.isArray, fonction](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf, fonction](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Constante undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md)   
 [Types de données](../../javascript/data-types-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)