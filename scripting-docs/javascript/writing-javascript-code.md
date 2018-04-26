---
title: Écriture de code JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>Écriture de code JavaScript
Comme de nombreux autres langages de programmation, le code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est organisé dans des instructions, à savoir des blocs constitués d’ensembles associés d’instructions et de commentaires. Dans une instruction, vous pouvez utiliser des variables, des chaînes, des nombres et des expressions.  
  
## <a name="statements"></a>Instructions  
 Un programme [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est une collection d’instructions. Les instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] combinent des expressions de telle sorte qu’elles effectuent une tâche complète.  
  
 Une instruction se compose d’une ou plusieurs mots clés, expressions ou opérateurs (symboles). En règle générale, une instruction est écrite sur une seule ligne, bien que vous puissiez l’écrire sur deux lignes ou plus. En outre, vous pouvez écrire plusieurs instructions sur la même ligne en les séparant par des points-virgules. En général, chaque nouvelle ligne commence une nouvelle instruction. Il est préférable de mettre fin à vos instructions de manière explicite. Vous utilisez pour cela le point-virgule (;), qui est le caractère de fin d’instruction [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Voici deux exemples d’instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Les phrases après les caractères // sont des *commentaires*, des notes explicatives dans le programme.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Un groupe d’instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] placées dans des accolades ({}) porte le nom de *bloc*. Les instructions groupées dans un bloc peuvent généralement être traitées comme une instruction unique. Cela signifie que vous pouvez utiliser des blocs presque partout où [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] attend une instruction unique. Les principales exceptions sont les en-têtes des boucles **for** et `while`. Notez que les différentes instructions au sein d’un bloc se terminent par des points-virgules, mais pas le bloc lui-même.  
  
 En règle générale, les blocs sont utilisés dans des fonctions et des instructions conditionnelles. Notez que contrairement à C++ et à d’autres langages, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ne considère pas un bloc comme une nouvelle étendue ; seules les fonctions créent une étendue.  
  
 Dans l’exemple suivant, la clause `else` contient un bloc de deux instructions placées entre accolades. Le bloc est traité comme une instruction unique. De plus, la fonction elle-même se compose d’un bloc d’instructions placées entre accolades. Les instructions sous la fonction sont en dehors du bloc et ne font donc pas partie de la définition de fonction.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Commentaires  
 Un commentaire [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sur une seule ligne commence par une paire de barres obliques (//). Voici un exemple de commentaire sur une seule ligne.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un commentaire [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] multiligne commence par une barre oblique et un astérisque (/\*), et se termine par l’inverse (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Si vous tentez d’incorporer un commentaire multiligne dans un autre, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interprète le commentaire multiligne obtenu de manière inattendue. Le */ qui marque la fin du commentaire multiligne incorporé est interprété comme la fin du commentaire multiligne entier. Cela signifie que le texte qui suit le commentaire multiligne incorporé n’est pas commenté ; au lieu de cela, il est interprété comme du code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] et il génère des erreurs de syntaxe.  
  
 Nous vous recommandons d’écrire tous vos commentaires sous forme de blocs de commentaires sur une seule ligne. Cela vous permet de commenter ultérieurement de grands segments de code avec un commentaire multiligne.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Assignations et égalité  
 Le signe égal (=) est utilisé dans les instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] pour assigner des valeurs à des variables : il s’agit de l’opérateur d’assignation. L’opérande gauche de l’opérateur = est toujours une Lvalue. Voici quelques exemples de Lvalues :  
  
-   Variables  
  
-   Éléments de tableau  
  
-   Propriétés d’objet  
  
 L’opérande droit de l’opérateur = est toujours une Rvalue. Les RValues peuvent être une valeur arbitraire de n’importe quel type, notamment la valeur d’une expression. Voici un exemple d’assignation d’instruction [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anInteger = 3;  
```  
  
 Le compilateur [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interprète cette instruction comme signifiant : « assigner la valeur 3 à la variable **anInteger** » ou « **anInteger** prend la valeur 3 ».  
  
 Veillez à bien comprendre la différence entre l’opérateur = (assignation) et l’opérateur == (égalité). Quand vous souhaitez comparer deux valeurs pour déterminer si elles sont égales, utilisez deux signes égal (==). Ceci est décrit en détail dans [Contrôle du flux de programme](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Expressions  
 Une valeur d’expression [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] peut être de n’importe quel type [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] valide : nombre, chaîne, objet, et ainsi de suite. Les expressions les plus simples sont des littéraux. Voici quelques exemples d’expressions littérales [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Les expressions plus complexes peuvent contenir des variables, des appels de fonction et d’autres expressions. Vous pouvez combiner des expressions pour créer des expressions complexes à l’aide d’opérateurs. Voici quelques exemples d’opérateurs : `+` (addition), `-` (soustraction), `*` (multiplication) et `/` (division).  
  
 Voici quelques exemples d’expressions complexes [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```