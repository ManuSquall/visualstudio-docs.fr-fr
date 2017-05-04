---
title: "conditionnel, op&#233;rateur (ternaire) (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "conditionnel (ternaire) (opérateur)"
  - "opérateurs conditionnels"
  - "ternaire"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# conditionnel, op&#233;rateur (ternaire) (?:) (JavaScript)
En fonction d'une condition, retourne l'une ou l'autre des deux expressions.  
  
## Syntaxe  
  
```  
  
test ? expression1 : expression2  
```  
  
## Paramètres  
 `test`  
 Toute expression booléenne.  
  
 `expression1`  
 Une expression retournée si `test` a la valeur `true`.  Il peut s'agir d'une expression avec virgules.  
  
 `expression2`  
 Une expression retournée si `test` a la valeur `false`.  Plusieurs expressions peuvent être liées par une expression avec virgules.  
  
## Notes  
 L'opérateur `?:` peut être utilisé comme raccourci pour une instruction `if...else`.  Il est généralement employé dans une expression plus longue où une instruction `if...else` ne serait pas appropriée.  Par exemple :  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 Cet exemple crée une chaîne contenant « Bonne soirée. » si elle est exécutée après 18 heures.  Le code équivalent avec l'instruction `if...else` se présenterait comme ceci :  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [if...else, instruction](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Exemple d'application de widget de configuration de Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)