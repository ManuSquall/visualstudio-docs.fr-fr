---
title: "Op&#233;rateurs (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, opérateurs"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Op&#233;rateurs (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inclut une gamme complète d'opérateurs : arithmétiques, logiques, de bits, d'assignation et bien d'autres encore.  Pour obtenir des explications et des exemples, consultez les rubriques relatives aux opérateurs spécifiques.  
  
## Opérateurs de calcul  
  
|Description|Symbole|  
|-----------------|-------------|  
|[Négation unaire](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[Increment](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[Decrement](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[Multiplication](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[Division](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[Modulo arithmétique](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Addition](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[Soustraction](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## Opérateurs logiques  
  
|Description|Symbole|  
|-----------------|-------------|  
|[NOT logique](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[Inférieur à](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Supérieur à](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[Inférieur ou égal à](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[Supérieur ou égal à](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[Égalité](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[Inégalité](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[AND logique](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR logique](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Conditionnel \(ternaire\)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Virgule](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Égalité stricte](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[Inégalité stricte](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## Opérateurs de bits  
  
|Description|Symbole|  
|-----------------|-------------|  
|[Opération de bits NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Décalage vers la gauche, opérateur de bits](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[Décalage vers la droite, opérateur de bits](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[Décalage vers la droite non signé](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[Opération de bits AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Opération de bits XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Opération de bits OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## Opérateurs d'assignation  
  
|Description|Symbole|  
|-----------------|-------------|  
|[Assignation](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[Assignation composée](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\= \(tel que \+\= et &\=\)|  
  
## Opérateurs divers  
  
|Description|Symbole|  
|-----------------|-------------|  
|[supprimer](../javascript/reference/delete-operator-decrementjavascript.md)|supprimer|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## Égalité et identité  
 La différence entre \=\= \(égalité\) et \=\=\= \(égalité stricte\) réside dans le fait que l'opérateur d'égalité forcera des valeurs de différents types avant d'effectuer le contrôle d'égalité.  Par exemple, lors de la comparaison de la chaîne « 1 » avec le nombre 1, la valeur retournée sera true.  L'opérateur d'égalité stricte, en revanche, ne forcera pas de valeurs de types différents. La chaîne « 1 » ne sera pas considérée comme équivalente au nombre 1.  
  
 Les chaînes primitives, les nombres et les valeurs booléennes sont comparés par valeur.  S'ils ont la même valeur, ils sont égaux.  Les objets \(y compris les objets `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` et `RegExp`\) sont comparés par référence.  Même si deux variables de ces types présentent la même valeur, elles sont égales uniquement si elles font exactement référence au même objet.  
  
 Par exemple :  
  
```javascript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```