---
title: "spread, op&#233;rateur (...) (JavaScript) | Microsoft Docs"
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# spread, op&#233;rateur (...) (JavaScript)
Permet aux parties d'un littéral de tableau d'être initialisées à partir d'une expression itérable \(par exemple, un autre littéral de tableau\), ou autorise une expression à être développée en plusieurs arguments \(dans les appels de fonction\).  
  
## Syntaxe  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## Paramètres  
 `iterable`  
 Obligatoire.  Objet itérable.  
  
 `arg0ToN`  
 Facultatif.  Un ou plusieurs éléments d'un littéral de tableau.  
  
 `args`  
 Facultatif.  Un ou plusieurs arguments d'une fonction.  
  
## Notes  
 Pour plus d'informations sur les itérateurs, consultez [Itérateurs et générateurs](../../javascript/advanced/iterators-and-generators-javascript.md).  Pour plus d'informations sur l'utilisation de l'opérateur spread comme paramètre rest, consultez [Fonctions](../../javascript/functions-javascript.md).  
  
## Exemple  
 Dans l'exemple de code suivant, l'utilisation de l'opérateur spread s'oppose à l'utilisation de la méthode `concat`.  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l'opérateur spread dans un appel de fonction.  Dans cet exemple, deux littéraux de tableaux sont passés à la fonction à l'aide de l'opérateur spread et les tableaux sont étendus à plusieurs arguments.  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## Exemple  
 Avec les opérateurs spread, vous pouvez simplifier le code qui nécessitait auparavant l'utilisation de `apply`.  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)