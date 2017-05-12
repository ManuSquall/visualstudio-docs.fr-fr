---
title: "return, instruction (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function (instruction)"
  - "return (instruction)"
  - "return (instruction), quitter les fonctions dans un script"
  - "return (instruction), syntaxe"
  - "terminer l'exécution"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return, instruction (JavaScript)
Quitte la fonction en cours et retourne une valeur de cette fonction.  
  
## Syntaxe  
  
```  
  
return[(][expression][)];   
```  
  
## Notes  
 L'argument *expression* facultatif est la valeur à retourner par la fonction.  Si elle est omise, la fonction ne retourne pas de valeur.  
  
 Vous utilisez l'instruction `return` pour arrêter l'exécution d'une fonction et retourner la valeur de l'argument *expression*.  Si l'argument *expression* est omis ou si aucune instruction `return` n'est exécutée à l'intérieur de la fonction, la valeur undefined est assignée à l'expression qui a appelé la fonction en cours.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `return`.  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `return` pour retourner une fonction.  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [function, instruction](../../javascript/reference/function-statement-javascript.md)