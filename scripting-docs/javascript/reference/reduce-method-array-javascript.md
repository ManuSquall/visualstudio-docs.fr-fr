---
title: "reduce, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), reduce (méthode)"
  - "callback (fonction), reduce (méthode) (JavaScript)"
  - "reduce (méthode) (JavaScript)"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce, m&#233;thode (Array) (JavaScript)
Appelle la fonction de rappel spécifiée pour tous les éléments d'un tableau.  La valeur de retour de la fonction de rappel est le résultat cumulé, et est fournie en tant qu'argument dans le prochain appel à la fonction de rappel.  
  
## Syntaxe  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau.|  
|`callbackfn`|Obligatoire.  Fonction qui accepte jusqu'à quatre arguments.  La méthode `reduce` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`initialValue`|Facultatif.  Si la valeur `initialValue` est spécifiée, elle est utilisé comme valeur initiale pour démarrer l'accumulation.  Le premier appel à la fonction `callbackfn` fournit cette valeur sous la forme d'un argument au lieu d'une valeur de tableau.|  
  
## Valeur de retour  
 Résultat cumulé du dernier appel à la fonction de rappel.  
  
## Exceptions  
 Une exception `TypeError` est levée lorsque l'une des conditions suivantes est vraie :  
  
-   L'argument `callbackfn` n'est pas un objet de fonction.  
  
-   Le tableau ne contient aucun élément et `initialValue` n'est pas fourni.  
  
## Notes  
 Si `initialValue` est fourni, la méthode `reduce` appelle la fonction `callbackfn` une fois pour chaque élément présent dans le tableau, dans l'ordre d'indexation croissant.  Si `initialValue` n'est pas fourni, la méthode `reduce` appelle la fonction `callbackfn` sur chaque élément, en commençant par le deuxième élément.  
  
 La valeur de retour de la fonction de rappel est fournie en tant qu'argument `previousValue` sur l'appel suivant à la fonction de rappel.  La valeur de retour du dernier appel à la fonction de rappel est la valeur de retour de la méthode `reduce`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
> [!NOTE]
>  La [reduceRight, méthode \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md) traite les éléments dont l'ordre d'indexation décroissant.  
  
## Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec quatre paramètres maximum.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Argument de rappel|Définition|  
|------------------------|----------------|  
|`previousValue`|Valeur de l'appel précédent à la fonction de rappel.  Si une valeur `initialValue` est fournie à la méthode `reduce`, `previousValue` correspond à `initialValue` lors du premier appel de la fonction.|  
|`currentValue`|Valeur de l'élément de tableau actuel.|  
|`currentIndex`|Index numérique de l'élément de tableau actuel.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## Premier appel à la fonction de rappel  
 Lors du premier appel de la fonction de rappel, les valeurs fournies en tant qu'arguments varient selon que la méthode `reduce` possède un argument `initialValue` ou non.  
  
 Si une valeur `initialValue` est fournie à la méthode reduce :  
  
-   L'argument `previousValue` correspond à `initialValue`.  
  
-   L'argument `currentValue` est la valeur du premier élément présent dans le tableau.  
  
 Si aucune valeur `initialValue` n'est indiquée :  
  
-   L'argument `previousValue` est la valeur du premier élément présent dans le tableau.  
  
-   L'argument `currentValue` est la valeur du deuxième élément présent dans le tableau.  
  
## Modification de l'objet tableau  
 L'objet tableau ne peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `reduce`.  
  
|Condition après le démarrage de la méthode `reduce`|Élément passé à la fonction de rappel ?|  
|---------------------------------------------------------|---------------------------------------------|  
|L'élément est ajouté au\-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## Exemple  
 L'exemple suivant concatène des valeurs de tableau en chaîne, en séparant les valeurs par « :: ».  Étant donné qu'aucune valeur initiale n'est fournie à la méthode `reduce`, le premier appel à la fonction de rappel utilise « abc » comme argument `previousValue` et « def » comme argument `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## Exemple  
 L'exemple suivant ajoute les valeurs d'un tableau une fois qu'elles ont été arrondies.  La méthode `reduce` est appelée avec une valeur initiale de 0.  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## Exemple  
 L'exemple suivant ajoute les valeurs dans un tableau.  Les paramètres `currentIndex` et `array1` sont utilisés dans la fonction de rappel.  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## Exemple  
 L'exemple suivant obtient un tableau qui contient uniquement les valeurs comprises entre 1 et 10 dans un autre tableau.  La valeur initiale fournie à la méthode `reduce` est un tableau vide.  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [reduceRight, méthode \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)