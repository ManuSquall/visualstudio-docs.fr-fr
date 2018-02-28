---
title: "Opérateurs (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>Opérateurs (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] offre une gamme complète d’opérateurs, notamment des opérations arithmétiques, logiques, au niveau du bit, d’attribution, ainsi que plusieurs opérateurs divers. Pour obtenir des explications et des exemples, consultez les rubriques relatives aux opérateurs en question.  
  
## <a name="computational-operators"></a>Opérateurs de calcul  
  
|Description|Symbole|  
|-----------------|------------|  
|[Négation unaire](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Incrément](../javascript/reference/increment-and-decrement-operators-javascript.md).|++|  
|[Décrément](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Multiplication](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[Division](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Modulo arithmétique](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Addition](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Soustraction](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Opérateurs logiques  
  
|Description|Symbole|  
|-----------------|------------|  
|[NOT logique](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Inférieur à](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Supérieur à](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Inférieur ou égal à](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Supérieur ou égal à](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Égalité](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Inégalité](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[AND logique](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR logique](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Conditionnel (ternaire)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Virgule](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Égalité stricte](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Inégalité stricte](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Opérateurs de bits  
  
|Description|Symbole|  
|-----------------|------------|  
|[NOT au niveau du bit](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Décalage vers la gauche au niveau du bit](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Décalage vers la droite au niveau du bit](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Décalage vers la droite non signé](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[AND au niveau du bit](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[XOR au niveau du bit](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[OR au niveau du bit](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Opérateurs d'assignation  
  
|Description|Symbole|  
|-----------------|------------|  
|[Attribution](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Affectation composée](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (comme += et &=)|  
  
## <a name="miscellaneous-operators"></a>Opérateurs divers  
  
|Description|Symbole|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|delete|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|dans|  
  
## <a name="equality-and-strict-equality"></a>Égalité et égalité stricte  
 La différence entre == (égalité) et === (égalité stricte) est que l’opérateur d’égalité force les valeurs de différents types avant de vérifier l’égalité. Par exemple, la comparaison de la chaîne « 1 » avec le nombre 1 donne la valeur true. L’opérateur d’égalité stricte, quant à lui, ne force pas les valeurs sur différents types. Ainsi, la chaîne « 1 » n’est pas considérée comme égale au nombre 1.  
  
 Les chaînes primitives, les nombres et les valeurs booléennes sont comparés par valeur. S’ils ont la même valeur, ils sont égaux. Les objets (notamment les objets `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` et `RegExp`) sont comparés par référence. Même si deux variables de ces types ont la même valeur, elles sont égales uniquement si elles font référence exactement au même objet.  
  
 Exemple :  
  
```JavaScript  
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