---
title: "function, instruction (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "déclarer des fonctions"
  - "déclarer des fonctions, syntaxe"
  - "function (instruction)"
  - "new (opérateur)"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function, instruction (JavaScript)
Déclare une nouvelle fonction.  
  
## Syntaxe  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## Paramètres  
 `functionname`  
 Obligatoire.  Nom de la fonction.  
  
 `arg1...argN`  
 Facultatif.  Liste facultative d'arguments séparés par des virgules, reconnus par la fonction.  
  
 `statements`  
 Facultatif.  Une ou plusieurs instructions de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Notes  
 Employez l'instruction `function` pour déclarer une fonction destinée à une utilisation ultérieure.  Le code contenu dans `statements` n'est pas exécuté tant que la fonction n'a pas été appelée depuis un emplacement différent dans le script.  
  
 L'instruction [return](../../javascript/reference/return-statement-javascript.md) est utilisée pour retourner une valeur de la fonction.  L'instruction `return` est inutile, le programme retourne une valeur lorsqu'il atteint la fin de la fonction.  Si aucune instruction `return` n'est exécutée dans la fonction, ou si l'instruction `return` n'a aucune expression, la fonction retourne la valeur `undefined`.  
  
> [!NOTE]
>  Lors de l'appel d'une fonction, veillez à inclure les parenthèses et les arguments requis.  Appeler une fonction sans parenthèses retourne une référence à la fonction, pas les résultats de la fonction.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `function`.  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## Exemple  
 Une fonction peut être assignée à une variable.  L'exemple suivant le montre.  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)