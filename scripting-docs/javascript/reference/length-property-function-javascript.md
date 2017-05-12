---
title: "length, propri&#233;t&#233; (Function) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length (propriété)"
  - "length (propriété) (Function)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length, propri&#233;t&#233; (Function) (JavaScript)
Obtient le nombre d'arguments définis pour une fonction.  
  
## Syntaxe  
  
```  
  
functionName.length  
```  
  
## Notes  
 Le *functionName* requis est le nom de la fonction.  
  
 La propriété **length** d'une fonction est initialisée par le moteur de script selon le nombre d'arguments définissant la fonction lorsqu'une instance de celle\-ci est créée.  
  
 Ce qui se produit lors de l'appel d'une fonction avec un nombre d'arguments qui ne correspond pas à la valeur de sa propriété **length** diffère selon la fonction considérée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété **length** :  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [arguments, propriété \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length, propriété \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriété length \(Chaîne\)](../../javascript/reference/length-property-string-javascript.md)