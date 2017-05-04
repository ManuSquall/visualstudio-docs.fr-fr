---
title: "length, propri&#233;t&#233; (arguments) (JavaScript) | Microsoft Docs"
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
  - "length (propriété) (arguments)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length, propri&#233;t&#233; (arguments) (JavaScript)
Retourne le nombre réel d'arguments passés à une fonction par l'appelant.  
  
## Syntaxe  
  
```  
[function.]arguments.length  
```  
  
## Notes  
 L'argument *function* facultatif est le nom de l'objet `Function` en cours d'exécution.  
  
 La propriété **length** de l'objet **arguments** est initialisée par le moteur de script sur le nombre réel d'arguments passés à un objet `Function` au début de l'exécution de cette fonction.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété **length** de l'objet **arguments**.  Pour comprendre parfaitement l'exemple, passez des arguments supplémentaires à la fonction, en plus des deux arguments attendus :  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [arguments, objet](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de function](../../javascript/reference/function-object-javascript.md)  
  
## Voir aussi  
 [arguments, propriété \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length, propriété \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriété length \(Chaîne\)](../../javascript/reference/length-property-string-javascript.md)