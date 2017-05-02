---
title: "arguments, propri&#233;t&#233; (Function) (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments, propriété arguments"
  - "Arguments (propriété)"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments, propri&#233;t&#233; (Function) (JavaScript)
Obtient les arguments pour l'objet `Function` en cours d'exécution.  
  
## Syntaxe  
  
```  
  
function.arguments  
```  
  
## Notes  
 L'argument `function` est le nom de la fonction en cours d'exécution, et peut être omis.  
  
 Cette propriété permet à une fonction de traiter un nombre variable d'arguments.  La propriété **length** de l'objet `arguments` contient le nombre d'arguments passés à la fonction.  Les différents arguments contenus dans l'objet `arguments` sont accessibles de la même manière que les éléments de tableau.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété `arguments` :  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [arguments, objet](../../javascript/reference/arguments-object-javascript.md)   
 [function, instruction](../../javascript/reference/function-statement-javascript.md)