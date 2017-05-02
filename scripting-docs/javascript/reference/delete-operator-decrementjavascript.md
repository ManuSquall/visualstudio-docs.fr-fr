---
title: "delete, op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "éléments de tableau, suppression"
  - "propriétés, suppression"
  - "Opérateur delete"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete, op&#233;rateur (JavaScript)
Supprime une propriété d'un objet ou supprime un élément d'un tableau.  
  
## Syntaxe  
  
```  
delete expression  
```  
  
## Notes  
 L'argument `expression` est une expression [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valide qui génère habituellement un nom de propriété ou un élément de tableau.  
  
 Si le résultat de l'argument `expression` est un objet, que la propriété spécifiée dans `expression` existe et que l'objet n'en permet pas la suppression, la valeur retournée est `false`.  
  
 Dans tous les autres cas, la valeur retournée est `true`.  
  
## Exemple  
 L'exemple suivant montre comment supprimer un élément d'un tableau.  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## Exemple  
 L'exemple suivant montre comment supprimer des propriétés d'un objet.  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)