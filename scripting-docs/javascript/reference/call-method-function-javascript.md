---
title: "call, m&#233;thode (Function) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call (méthode)"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# call, m&#233;thode (Function) (JavaScript)
Appelle une méthode d'objet et remplace l'objet en cours par un autre.  
  
## Syntaxe  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## Paramètres  
 `thisObj`  
 Optionnel.  Objet à utiliser comme objet en cours.  
  
 `arg1, arg2, , argN`  
 Optionnel.  Liste d'arguments à passer à la méthode.  
  
## Notes  
 La méthode `call` est utilisée pour appeler une méthode pour le compte d'un autre objet.  Elle permet de remplacer l'objet `this` d'une fonction du contexte d'origine par le nouvel objet spécifié par `thisObj`.  
  
 Si l'argument `thisObj` n'est pas spécifié, l'objet `global` est utilisé pour `thisObj`.  
  
## Exemple  
 Le code suivant montre comment utiliser la méthode `call`.  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [apply, méthode \(Function\)](../../javascript/reference/apply-method-function-javascript.md)