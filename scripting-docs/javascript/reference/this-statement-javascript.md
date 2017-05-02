---
title: "this, instruction (JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructeurs, référence à l'objet actuel"
  - "this (instruction)"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this, instruction (JavaScript)
Fait référence à l'objet en cours.  
  
## Syntaxe  
  
```  
this.property  
```  
  
## Notes  
 L'argument `property` requis est l'une des propriétés de l'objet actif  
  
 Le mot clé `this` peut être employé dans des constructeurs d'objet pour faire référence à l'objet actif.  
  
## Exemple  
 Dans l'exemple suivant, **this** fait référence au nouvel objet Car et assigne des valeurs à trois propriétés :  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Le mot clé **this** désigne généralement l'objet **fenêtre** s'il est utilisé en dehors de la portée de tout autre objet.  Toutefois, dans les gestionnaires d'événements `this` fait référence à l'élément DOM qui a déclenché l'événement.  
  
 Dans le code suivant \(pour Internet Explorer 9 et versions ultérieures\), le gestionnaire d'événements imprime la version chaîne d'un bouton qui a un ID de « cliqueur ».  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Utilisation de la méthode Bind](../../javascript/advanced/using-the-bind-method-javascript.md)