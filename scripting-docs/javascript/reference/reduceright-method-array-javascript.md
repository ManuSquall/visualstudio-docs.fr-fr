---
title: "reduceRight, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), reduceRight (méthode)"
  - "reduceRight (méthode) (JavaScript)"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight, m&#233;thode (Array) (JavaScript)
Appelle la fonction de rappel spécifiée pour tous les éléments d'un tableau, dans l'ordre décroissant.  La valeur de retour de la fonction de rappel est le résultat cumulé, et est fournie en tant qu'argument dans le prochain appel à la fonction de rappel.  
  
## Syntaxe  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau.|  
|`callbackfn`|Obligatoire.  Fonction qui accepte jusqu'à quatre arguments.  La méthode `reduceRight` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`initialValue`|Facultatif.  Si la valeur `initialValue` est spécifiée, elle est utilisé comme valeur initiale pour démarrer l'accumulation.  Le premier appel à la fonction `callbackfn` fournit cette valeur sous la forme d'un argument au lieu d'une valeur de tableau.|  
  
## Valeur de retour  
 Objet contenant le résultat accumulé du dernier appel à la fonction de rappel.  
  
## Exceptions  
 Une exception `TypeError` est levée lorsque l'une des conditions suivantes est vraie :  
  
-   L'argument `callbackfn` n'est pas un objet de fonction.  
  
-   Le tableau ne contient aucun élément et `initialValue` n'est pas fourni.  
  
## Notes  
 Si `initialValue` est fourni, la méthode `reduceRight` appelle la fonction `callbackfn` une fois pour chaque élément dans le tableau, dans l'ordre d'indexation décroissant.  Si aucun `initialValue` n'est fourni, la méthode `reduceRight` appelle la fonction `callbackfn` sur chaque élément, en commençant par l'avant\-dernier, dans l'ordre d'indexation décroissant.  
  
 La valeur de retour de la fonction de rappel est fournie en tant qu'argument `previousValue` sur l'appel suivant à la fonction de rappel.  La valeur de retour du dernier appel à la fonction de rappel est la valeur de retour de la méthode `reduceRight`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Pour accumuler un résultat dans l'ordre d'indexation ascendant, utilisez la [reduce, méthode \(Array\)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec quatre paramètres maximum.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Argument de rappel|Définition|  
|------------------------|----------------|  
|`previousValue`|Valeur de l'appel précédent à la fonction de rappel.  Si `initialValue` est fourni à la méthode `reduceRight`, `previousValue` correspond à `initialValue` lors du premier appel de la fonction.|  
|`currentValue`|Valeur de l'élément de tableau actuel.|  
|`currentIndex`|Index numérique de l'élément de tableau actuel.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## Premier appel à la fonction de rappel  
 Lors du premier appel de la fonction de rappel, les valeurs fournies en tant qu'arguments varient selon que la méthode `reduceRight` possède un argument `initialValue` ou non.  
  
 Si `initialValue` est fourni à la méthode `reduceRight` :  
  
-   L'argument `previousValue` correspond à `initialValue`.  
  
-   L'argument `currentValue` est la valeur du dernier élément présent dans le tableau.  
  
 Si aucune valeur `initialValue` n'est indiquée :  
  
-   L'argument `previousValue` est la valeur du dernier élément présent dans le tableau.  
  
-   L'argument `currentValue` est la valeur de l'avant\-dernier élément présent dans le tableau.  
  
## Modification de l'objet tableau  
 L'objet tableau ne peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `reduceRight`.  
  
|Condition après le démarrage de la méthode `reduceRight`|Élément passé à la fonction de rappel ?|  
|--------------------------------------------------------------|---------------------------------------------|  
|L'élément est ajouté au\-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## Exemple  
 L'exemple suivant concatène des valeurs de tableau en chaîne, en séparant les valeurs par « :: ».  Étant donné qu'aucune valeur initiale n'est fournie à la méthode `reduceRight`, le premier appel à la fonction de rappel utilise « 456 » comme argument `previousValue` et « 123 » comme argument `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## Exemple  
 L'exemple suivant trouve la somme des carrés des éléments de tableau.  La méthode `reduceRight` est appelée avec une valeur initiale de 0.  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## Exemple  
 L'exemple suivant obtient les éléments d'un tableau dont les valeurs sont entre 1 et 10.  La valeur initiale fournie à la méthode `reduceRight` est un tableau vide.  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## Exemple  
 La méthode `reduceRight` peut être appliquée à une chaîne.  L'exemple suivant montre comment utiliser cette méthode pour inverser les caractères d'une chaîne.  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [reduce, méthode \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)