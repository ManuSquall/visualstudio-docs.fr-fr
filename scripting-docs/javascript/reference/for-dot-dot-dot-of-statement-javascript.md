---
title: "for...of, instruction (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# for...of, instruction (JavaScript)
Exécute une ou plusieurs instructions pour chaque valeur d'un itérateur obtenu à partir d'un objet pouvant être itéré.  
  
## Syntaxe  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## Paramètres  
 `variable`  
 Obligatoire.  Variable qui peut être toute valeur de propriété d'`object`.  
  
 `object`  
 Obligatoire.  Objet pouvant être itéré, comme `Array`, `Map`, `Set`, ou objet qui implémente les [interfaces d'itérateur](http://msdn.microsoft.com/fr-fr/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Facultatif.  Une ou plusieurs instructions à exécuter pour chaque valeur d'un `object`.  Il peut s'agir d'une instruction composée.  
  
## Notes  
 Au début de chaque itération d'une boucle, la valeur de `variable` est la valeur de propriété suivante d'`object`.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `for...of` sur un tableau.  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `for...of` sur un objet `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [for...in, instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for, instruction](../../javascript/reference/for-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)