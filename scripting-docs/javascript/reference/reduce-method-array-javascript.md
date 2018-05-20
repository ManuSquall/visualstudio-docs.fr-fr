---
title: Reduce, méthode (Array) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d99f92d90885f26b19392b476ee64ae17bd40aed
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="reduce-method-array-javascript"></a>reduce, méthode (Array) (JavaScript)
Appelle la fonction de rappel spécifiée pour tous les éléments dans un tableau. La valeur de retour de la fonction de rappel est le résultat accumulé, et est fournie en tant qu’argument dans le prochain appel à la fonction de rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Une fonction qui accepte jusqu'à quatre arguments. La méthode `reduce` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`initialValue`|Facultatif. Si `initialValue` est spécifié, il est utilisé comme valeur initiale pour démarrer l’accumulation. Le premier appel à la `callbackfn` fonction fournit cette valeur en tant qu’argument à la place d’une valeur de tableau.|  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat accumulé du dernier appel à la fonction de rappel.  
  
## <a name="exceptions"></a>Exceptions  
 A `TypeError` exception est levée lorsque une des conditions suivantes est vraie :  
  
-   Le `callbackfn` argument n’est pas un objet de fonction.  
  
-   Le tableau ne contient aucun élément et `initialValue` n’est pas fourni.  
  
## <a name="remarks"></a>Notes  
 Si un `initialValue` est fourni, le `reduce` les appels de méthode du `callbackfn` fonction une fois pour chaque élément présent dans le tableau, dans l’ordre d’index croissant. Si un `initialValue` n’est pas fourni, le `reduce` les appels de méthode du `callbackfn` fonction sur chaque élément, en commençant par le deuxième élément.  
  
 La valeur de retour de la fonction de rappel est fournie en tant que le `accumulator` argument sur le prochain appel à la fonction de rappel. La valeur de retour du dernier appel à la fonction de rappel est la valeur de retour de la `reduce` (méthode).  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
> [!NOTE]
>  Le [reduceright, méthode (Array)](../../javascript/reference/reduceright-method-array-javascript.md) traite les éléments dans l’ordre d’index décroissant.  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(accumulator, currentValue, currentIndex, array1)`  
  
 Vous pouvez déclarer la fonction de rappel à l’aide de quatre paramètres.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`accumulator`|La valeur de l’appel précédent à la fonction de rappel. Si un `initialValue` est fournie pour le `reduce` (méthode), la `accumulator` est `initialValue` la première fois que la fonction est appelée.|  
|`currentValue`|La valeur de l’élément de tableau en cours.|  
|`currentIndex`|Index numérique de l’élément de tableau en cours.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## <a name="first-call-to-the-callback-function"></a>Premier appel à la fonction de rappel  
 La première fois que la fonction de rappel est appelée, les valeurs fournies comme arguments varient le `reduce` méthode a un `initialValue` argument.  
  
 Si un `initialValue` est fournie à la méthode de réduction :  
  
-   L'argument `accumulator` a la valeur `initialValue`.  
  
-   Le `currentValue` argument est la valeur du premier élément présent dans le tableau.  
  
 Si un `initialValue` n’est pas fourni :  
  
-   Le `accumulator` argument est la valeur du premier élément présent dans le tableau.  
  
-   Le `currentValue` argument est la valeur du deuxième élément présent dans le tableau.  
  
## <a name="modifying-the-array-object"></a>Modification de l'objet tableau  
 L'objet tableau peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `reduce`.  
  
|Condition après le démarrage de la méthode `reduce`|Élément passé à la fonction de rappel ?|  
|------------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant concatène les valeurs de tableau dans une chaîne en séparant les valeurs avec « :: ». Car aucune valeur initiale n’est fournie pour le `reduce` (méthode), le premier appel à la fonction de rappel a « abc » en tant que le `accumulator` argument et « def » comme le `currentValue` argument.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (accumulator, currentValue) {  
    return accumulator + "::" + currentValue;  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute les valeurs d’un tableau, une fois qu’ils ont été arrondis. Le `reduce` méthode est appelée avec une valeur initiale de 0.  
  
```JavaScript  
// Define the callback function.  
function addRounded (accumulator, currentValue) {  
    return accumulator + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute les valeurs dans un tableau. Le `currentIndex` et `array1` paramètres sont utilisés dans la fonction de rappel.  
  
```JavaScript  
function addDigitValue(accumulator, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return accumulator + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient un tableau qui contient des valeurs qui sont comprises entre 1 et 10 dans un autre tableau. La valeur initiale de la `reduce` méthode est un tableau vide.  
  
```JavaScript  
function Process(accumulatedArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = accumulatedArray.concat(currentValue);  
    else  
        nextArray = accumulatedArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is accumulatedArray on the next call.  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md)
