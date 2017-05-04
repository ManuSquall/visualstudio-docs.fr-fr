---
title: "if...else, instruction (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if (instruction), if...else"
  - "structures de boucle, if...else (instructions)"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else, instruction (JavaScript)
Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.  
  
## Syntaxe  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## Paramètres  
 `condition1`  
 Obligatoire.  Expression booléenne.  Si `condition1` est `null` ou `undefined`, `condition1` est traité comme `false`.  
  
 `statement1`  
 Facultatif.  Instruction à exécuter si `condition1` a la valeur **true**.  Il peut s'agir d'une instruction composée.  
  
 `condition2`  
 Condition à évaluer.  
  
 `statement2`  
 Facultatif.  Instruction à exécuter si `condition2` a la valeur `true`.  Il peut s'agir d'une instruction composée.  
  
 `statement3`  
 Si `condition1` et `condition2` sont `false`, cette instruction est exécutée.  
  
## Exemple  
 Le code suivant montre comment utiliser `if`, `if else` et `else`.  
  
 Pour plus de clarté et afin d'éviter les erreurs, il est conseillé de placer `statement1` et `statement2` entre accolades \({}\).  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [?: \(conditionnel ternaire\), opérateur](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)