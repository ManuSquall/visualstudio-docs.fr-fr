---
title: "arguments, objet (JavaScript) | Microsoft Docs"
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
  - "objets d'arguments"
  - "arguments, objets d'arguments"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments, objet (JavaScript)
Objet représentant les arguments passés à la fonction en cours d'exécution, ainsi que les fonctions qui l'ont appelé.  
  
## Syntaxe  
  
```  
[function.]arguments[n]  
```  
  
## Paramètres  
 *fonction*  
 Optionnel.  Nom de l'objet `Function` en cours d'exécution.  
  
 *n*  
 Requis.  Index de base zéro des valeurs d'argument passées à l'objet `Function`.  
  
## Notes  
 Vous ne pouvez pas créer un objet **arguments** de manière explicite.  L'objet **arguments** est uniquement disponible lorsque l'exécution d'une fonction commence.  L'objet **arguments** de la fonction n'est pas un tableau, mais les arguments individuels sont accessibles de la même manière que les éléments de tableau.  L'index *n* est en fait une référence à l'une des propriétés **0** ***n*** de l'objet **arguments**.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'objet **arguments** :  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [0...n, propriétés \(arguments\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee, propriété \(arguments\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length, propriété \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)