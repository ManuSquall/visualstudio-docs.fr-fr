---
title: "Fonctions (JavaScript) | Microsoft Docs"
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
  - "fonctions intrinsèques de JavaScript"
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Fonctions (JavaScript)
Les fonctions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] exécutent des actions et peuvent également retourner des valeurs.  Parfois, il s'agit du résultat d'un calcul ou d'une comparaison.  Les fonctions sont également appelées « méthodes globales ».  
  
 Les fonctions combinent plusieurs opérations sous un même nom.  Cela vous permet de simplifier votre code.  Vous pouvez rédiger un ensemble d'instructions, le nommer, puis exécuter l'ensemble en l'appelant et en lui passant toutes les informations requises.  
  
 Pour passer des informations à une fonction, vous devez les mettre entre parenthèses à la suite du nom de la fonction.  Les informations passées à une fonction sont appelées arguments ou paramètres.  Certaines fonctions ne requièrent pas d'argument, alors que d'autres exigent la présence d'un ou de plusieurs d'entre eux.  Dans certaines fonctions, le nombre d'arguments dépend de la manière dont vous utilisez la fonction.  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend en charge deux types de fonctions : celles qui sont intégrées au langage et celles que vous créez.  
  
## Fonctions intégrées  
 Le langage [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inclut plusieurs fonctions intégrées.  Certaines d'entre elles permettent de gérer des expressions et des caractères spéciaux, tandis que d'autres convertissent des chaînes en valeurs numériques.  
  
 Pour plus d'informations sur les fonctions intégrées, consultez [Méthodes JavaScript](../javascript/reference/javascript-methods.md).  
  
## Création de vos propres fonctions  
 Vous pouvez créer vos propres fonctions et les utiliser quand cela est nécessaire.  La définition d'une fonction comprend une instruction de fonction et un bloc d'instructions [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 La fonction **checkTriplet** de l'exemple suivant accepte comme arguments les longueurs des côtés d'un triangle.  Elle calcule, à partir de ces longueurs, si le triangle est rectangle en contrôlant si les trois nombres vérifient le théorème de Pythagore \(le carré de la longueur de l'hypoténuse d'un triangle rectangle est égal à la somme des carrés des longueurs des deux autres côtés\).  La fonction checkTriplet appelle l'une des deux autres fonctions pour effectuer le test.  
  
 Notez l'utilisation d'un tout petit nombre \(« epsilon »\) en guise de variable de test dans la version à virgule flottante du test.  En raison des incertitudes et des erreurs d'arrondi dans les calculs à virgule flottante, il n'est pas pratique d'effectuer un test direct pour contrôler si les trois nombres vérifient le théorème de Pythagore sauf dans le cas où ces trois valeurs sont des entiers.  Un test direct étant plus précis, le code de cet exemple détermine si ce test est approprié, et si c'est le cas, l'utilise.  
  
```javascript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## Fonctions Arrow  
 La syntaxe de fonction Arrow, `=>`, fournit une méthode abrégée de spécification d'une fonction anonyme.  Voici la syntaxe de fonction Arrow.  
  
```javascript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Les valeurs à gauche de la flèche, qui peuvent être mises entre parenthèses, spécifient les arguments passés à la fonction.  Un seul argument de la fonction ne nécessite pas de parenthèses.  Les parenthèses sont nécessaires si aucun argument n'est passé.  La définition de fonction à droite de la flèche peut être une expression, telle que `v + 1`, ou un bloc d'instructions placées entre accolades \({}\).  
  
> [!IMPORTANT]
>  La syntaxe de fonction Arrow est prise en charge uniquement en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Vous ne pouvez pas utiliser l'opérateur `new` avec une fonction Arrow.  
  
 Les exemples de code suivants illustrent l'utilisation de la fonction Arrow avec des expressions en tant que définitions de fonctions.  Dans le premier exemple, v est transmis comme argument à l'expression.  Dans le second exemple, v et i sont transmis comme arguments à l'expression.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 L'exemple de code suivant illustre l'utilisation de la fonction Arrow avec un bloc d'instructions.  
  
```javascript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 Contrairement aux fonctions standard, les fonctions Arrow partagent le même objet `this` lexical en tant que code environnant, qui peut être utilisé pour éliminer le besoin de solutions de contournement telles que `var self = this;`.  
  
 L'exemple suivant montre que la valeur de l'objet `this` dans la fonction Arrow est identique à celle du code environnant \(elle fait toujours référence à la variable `bob`\).  
  
```javascript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Les fonctions Arrow partagent également le même objet `arguments` lexical en tant que code environnant \(comme l'objet `this`\).  
  
<a name="Default"></a>   
## Paramètres par défaut  
 Vous pouvez spécifier une valeur par défaut pour un paramètre dans une fonction en lui assignant une valeur initiale.  La valeur par défaut peut être une valeur constante ou une expression.  
  
> [!IMPORTANT]
>  Les paramètres par défaut sont pris en charge uniquement en [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)].  
  
 Dans l'exemple suivant, la valeur par défaut de y est 10 et la valeur par défaut de z est 20.  La fonction utilise 10 comme valeur de y, sauf si l'appelant transmet une valeur distincte \(ou non définie\) comme deuxième argument.  La fonction utilise 20 comme valeur de z, sauf si l'appelant transmet une valeur distincte \(ou non définie\) comme troisième argument.  
  
```javascript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## Paramètres REST  
 Les paramètres rest, spécifiés par l'opérateur spread \(                       ``  \), vous permettent de convertir des arguments consécutifs d'un appel de fonction en tableau.  
  
 Les paramètres rest éliminent le besoin d'utiliser l'objet `arguments`.  Les paramètres rest présentent des différences par rapport à l'objet `arguments`, notamment :  
  
-   Un paramètre rest est une instance de tableau réel et par conséquent prend en charge les opérations qui peuvent être effectuées sur un tableau.  
  
-   Un paramètre rest inclut uniquement les arguments consécutifs qui ne sont pas transmis en tant qu'arguments distincts \(nommés\) \(à l'inverse, l'objet `arguments` contient tous les arguments transmis à la fonction\).  
  
> [!IMPORTANT]
>  Les paramètres rest et l'opérateur spread sont pris en charge uniquement en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Dans l'exemple de code suivant, "hello" et true sont transmis en tant que valeurs de tableau et stockés dans le paramètre y.  Le paramètre rest doit être le dernier paramètre de la fonction.  
  
```javascript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Pour connaître d'autres utilisations de l'opérateur spread, consultez [Opérateur spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## Voir aussi  
 [Informations de référence sur le langage JavaScript](../javascript/javascript-language-reference.md)