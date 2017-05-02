---
title: "Instruction for...in (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instructions d'itération, for...in (instruction)"
  - "structures de boucle, instructions for...in"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Instruction for...in (JavaScript)
Exécute une ou plusieurs instructions pour chaque propriété d'un objet ou chaque élément d'un tableau.  
  
## Syntaxe  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## Paramètres  
 `variable`  
 Obligatoire.  Variable qui peut être n'importe quel nom de propriété d'`object` ou n'importe quel index d'élément d'un `array`.  
  
 `object`, `array`  
 Facultatif.  Objet ou tableau au sein duquel itérer.  
  
 `statements`  
 Facultatif.  Une ou plusieurs instructions à exécuter pour chaque propriété d'`object` ou chaque élément d'`array`.  Il peut s'agir d'une instruction composée.  
  
## Notes  
 Au début de chaque itération d'une boucle, la valeur `variable` est le prochain nom de propriété d'`object` ou l'index d'élément suivant d'`array`.  Vous pouvez ensuite utiliser `variable` dans n'importe laquelle des instructions incluses dans la boucle pour référencer la propriété d'`object` ou l'élément d'`array`.  
  
 Les propriétés d'un objet ne sont pas assignées de façon déterminée.  Vous ne pouvez pas spécifier une propriété particulière par son index, mais uniquement par le nom de la propriété.  
  
 L'itération au sein d'un tableau est effectuée dans l'ordre des éléments, autrement dit, 0, 1, 2.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `for...in` avec un objet utilisé comme tableau associatif.  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'instruction `for ... in` pour itérer au sein d'un objet `Array` qui a des propriétés expando.  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Utilisez l'objet `Enumerator` pour itérer au sein des membres d'une collection.  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)