---
title: "&#201;criture de code JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "code, Syntaxe JavaScript"
  - "commentaires, Code JavaScript"
  - "Code JavaScript"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# &#201;criture de code JavaScript
Comme de nombreux autres langages de programmation, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est organisé en instructions, en blocs constitués de groupes d'instructions associés et en commentaires.  Il est possible d'utiliser des variables, des chaînes, des nombres et des expressions au sein d'une instruction.  
  
## Instructions  
 Un programme [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est une collection d'instructions.  Les instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] combinent des expressions de manière à n'effectuer qu'une seule et même tâche.  
  
 Une instruction comprend un ou plusieurs mots clés, expressions ou opérateurs \(symboles\).  En général, une instruction s'écrit sur une seule ligne. Elle peut, toutefois, s'écrire sur plusieurs lignes.  En outre, il est possible d'écrire plusieurs instructions sur une même ligne en les séparant par des points\-virgules.  En général, à chaque nouvelle ligne commence une nouvelle instruction.  Il est conseillé de terminer vos instructions de façon explicite.  Pour cela, utilisez un point\-virgule \(;\), qui est le caractère prévu à cet effet dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Voici deux exemples d'instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Les phrases situées après les caractères \/\/ sont des *commentaires*, qui sont des notes explicatives concernant le programme.  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Un groupe d'instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] délimité par des accolades \({}\) est appelé un *bloc*.  Les instructions regroupées au sein d'un bloc peuvent généralement être considérées comme une seule et même instruction.  Cela signifie que vous pouvez utiliser les blocs à la plupart des endroits où [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] attend une instruction unique.  Il existe quelques exceptions notables, dont les en\-têtes des boucles **for** et `while`.  Notez que les instructions uniques du bloc se terminent par un point\-virgule ; ce n'est pas le cas du bloc.  
  
 En règle générale, les blocs sont utilisés dans des fonctions et des conditions.  Notez qu'à la différence du C\+\+ et d'autres langages, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ne considère pas un bloc comme une nouvelle portée ; seules les fonctions peuvent créer une nouvelle portée.  
  
 Dans l'exemple suivant, la clause `else` contient un bloc de deux instructions entourées par des accolades.  Le bloc est traité comme une instruction unique.  En outre, la fonction est composée d'un bloc d'instructions entourées par des accolades.  Les instructions situées sous la fonction se trouvent en dehors du bloc et ne font donc pas partie de la définition de la fonction.  
  
```javascript  
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
  
## Commentaires  
 Un commentaire [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] d'une seule ligne commence par deux barres obliques \(\/\/\).  Voici un exemple de commentaire sur une seule ligne.  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un commentaire [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] multiligne commence par une barre oblique suivie d'un astérisque \(\/\*\) et se termine par un astérisque suivi d'une barre oblique \(\*\/\).  
  
```javascript  
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
>  Si vous tentez d'incorporer un commentaire multiligne dans un autre, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interprète le commentaire multiligne obtenu de manière inattendue.  Le symbole \*\/ qui marque la fin d'un commentaire multiligne incorporé est interprété comme la fin de tout le commentaire multiligne.  Cela signifie que le texte qui suit le commentaire multiligne incorporé ne sera pas commenté, mais interprété comme du code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], ce qui générera des erreurs de syntaxe.  
  
 Il est conseillé d'écrire tous les commentaires sous la forme de blocs de commentaires d'une seule ligne.  Ainsi, vous pourrez, par la suite, commenter des segments importants de code à l'aide d'un seul commentaire multiligne.  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## Assignations et égalité  
 Le signe égal \(\=\) est utilisé dans les instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] afin d'assigner des valeurs aux variables. Il s'agit de l'opérateur d'assignation.  L'opérande de gauche de l'opérateur \= est toujours une valeur lvalue.  Voici quelques exemples de lvalue :  
  
-   Variables  
  
-   Éléments de tableau  
  
-   Propriétés d'objet  
  
 L'opérande de droite de l'opérateur \= est toujours une valeur rvalue.  Les valeurs rvalue peuvent être des valeurs arbitraires de n'importe quel type, y compris la valeur d'une expression.  L'exemple suivant illustre une instruction d'assignation [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anInteger = 3;  
```  
  
 Le compilateur [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interprète cette instruction de la façon suivante : « Assigner la valeur 3 à la variable **anInteger** » ou « **anInteger** prend la valeur 3 ».  
  
 Il est important de bien comprendre la différence entre l'opérateur d'assignation \(\=\) et l'opérateur d'égalité \(\=\=\).  Lorsque vous souhaitez comparer deux valeurs pour déterminer si elles sont égales, utilisez deux signes égal \(\=\=\).  Cette opération est décrite en détail dans [Contrôle du flux du programme](../javascript/controlling-program-flow-javascript.md).  
  
## Expressions  
 Une valeur d'expression [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] peut correspondre à tout type [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] valide, soit un nombre, une chaîne, un objet, etc.  Les expressions les plus simples sont les expressions littérales.  Voici quelques exemples d'expressions littérales [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Des expressions plus complexes peuvent contenir des variables, des appels de fonction et d'autres expressions.  Vous pouvez avoir recours à des opérateurs pour combiner des expressions et créer des expressions complexes.  Voici quelques exemples d'opérateurs : `+` \(addition\), `-` \(soustraction\), `*` \(multiplication\) et `/` \(division\).  
  
 Voici quelques exemples d'expressions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] complexes.  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```