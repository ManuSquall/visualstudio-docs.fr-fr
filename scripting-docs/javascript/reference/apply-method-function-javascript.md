---
title: "apply, m&#233;thode (Function) (JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply (méthode)"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# apply, m&#233;thode (Function) (JavaScript)
Appelle la fonction, en substituant l'objet spécifié avec la valeur `this` de la fonction, et le tableau spécifié avec les arguments de la fonction.  
  
## Syntaxe  
  
```  
apply([thisObj[,argArray]])  
```  
  
## Paramètres  
 `thisObj`  
 Facultatif.  Objet à utiliser comme l'objet `this`.  
  
 `argArray`  
 Facultatif.  Ensemble d'arguments à passer à la fonction.  
  
## Notes  
 Si `argArray` n'est pas un objet valide, une erreur « Objet attendu » se produit.  
  
 Si ni l'argument `argArray`, ni l'argument `thisObj` ne sont fournis, l'objet `this` original est utilisé en tant que `thisObj` et aucun argument n'est passé.  
  
## Exemple  
 Le code suivant illustre l'utilisation de la méthode apply.  
  
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
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)