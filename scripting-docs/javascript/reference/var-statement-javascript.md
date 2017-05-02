---
title: "var, instruction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "déclaration de variables, var (instruction)"
  - "var (instruction)"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var, instruction (JavaScript)
Déclare une variable.  
  
## Syntaxe  
  
```  
var variable1 = value1  
```  
  
## Paramètres  
 `variable1`  
 Nom de la variable en cours de déclaration.  
  
 `value1`  
 Valeur initiale assignée à la variable.  
  
## Notes  
 Utilisez l'instruction `var` pour déclarer des variables.  Vous pouvez assigner des valeurs aux variables au moment de leur déclaration ou ultérieurement dans votre script.  
  
 Une variable est déclarée à sa première apparition dans votre script.  
  
 Vous pouvez déclarer une variable sans utiliser le mot clé `var` et lui assigner une valeur.  Il s'agit d'une *déclaration implicite*, peu recommandée.  Une déclaration implicite donne la portée globale de la variable.  Toutefois, lorsque vous déclarez une variable au niveau de la procédure, vous ne souhaitez généralement pas qu'elle ait une portée globale.  Pour éviter de donner une portée globale à la variable, vous devez utiliser le mot clé `var` dans votre déclaration de variable.  
  
 Si vous n'initialisez pas votre variable dans l'instruction `var`, la valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] `undefined` lui est automatiquement attribuée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'instruction `var`.  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [function, instruction](../../javascript/reference/function-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)