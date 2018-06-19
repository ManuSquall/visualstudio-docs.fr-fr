---
title: reduceright, méthode (Array) (JavaScript) | Documents Microsoft
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641919"
---
# <a name="reduceright-method-array-javascript"></a>reduceRight, méthode (Array) (JavaScript)
Appelle la fonction de rappel spécifiée pour tous les éléments dans un tableau, dans l’ordre décroissant. La valeur de retour de la fonction de rappel est le résultat accumulé, et est fournie en tant qu’argument dans le prochain appel à la fonction de rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Une fonction qui accepte jusqu'à quatre arguments. La méthode `reduceRight` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`initialValue`|Facultatif. Si `initialValue` est spécifié, il est utilisé comme valeur initiale pour démarrer l’accumulation. Le premier appel à la `callbackfn` fonction fournit cette valeur en tant qu’argument à la place d’une valeur de tableau.|  
  
## <a name="return-value"></a>Valeur de retour  
 Objet qui contient le résultat accumulé du dernier appel à la fonction de rappel.  
  
## <a name="exceptions"></a>Exceptions  
 A `TypeError` exception est levée lorsque une des conditions suivantes est vraie :  
  
-   Le `callbackfn` argument n’est pas un objet de fonction.  
  
-   Le tableau ne contient aucun élément et `initialValue` n’est pas fourni.  
  
## <a name="remarks"></a>Remarques  
 Si un `initialValue` est fourni, le `reduceRight` les appels de méthode le `callbackfn` fonction une fois pour chaque élément du tableau, dans l’ordre d’index décroissant. Si aucun `initialValue` est fourni, le `reduceRight` les appels de méthode du `callbackfn` fonction sur chaque élément, en commençant par l’élément de la dernière seconde, dans l’ordre d’index décroissant.  
  
 La valeur de retour de la fonction de rappel est fournie en tant que le `previousValue` argument sur le prochain appel à la fonction de rappel. La valeur de retour du dernier appel à la fonction de rappel est la valeur de retour de la `reduceRight` (méthode).  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Afin de réunir un résultat dans l’ordre d’index croissant, utilisez le [reduce, méthode (Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Vous pouvez déclarer la fonction de rappel à l’aide de quatre paramètres.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`previousValue`|La valeur de l’appel précédent à la fonction de rappel. Si un `initialValue` est fournie pour le `reduceRight` (méthode), la `previousValue` est `initialValue` la première fois que la fonction est appelée.|  
|`currentValue`|La valeur de l’élément de tableau en cours.|  
|`currentIndex`|Index numérique de l’élément de tableau en cours.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## <a name="first-call-to-the-callback-function"></a>Premier appel à la fonction de rappel  
 La première fois que la fonction de rappel est appelée, les valeurs fournies comme arguments varient le `reduceRight` méthode a un `initialValue` argument.  
  
 Si un `initialValue` est fourni à la `reduceRight` méthode :  
  
-   L'argument `previousValue` a la valeur `initialValue`.  
  
-   Le `currentValue` argument est la valeur du dernier élément présent dans le tableau.  
  
 Si un `initialValue` n’est pas fourni :  
  
-   Le `previousValue` argument est la valeur du dernier élément présent dans le tableau.  
  
-   Le `currentValue` argument est la valeur de l’élément de la dernière seconde présent dans le tableau.  
  
## <a name="modifying-the-array-object"></a>Modification de l'objet tableau  
 L'objet tableau peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `reduceRight`.  
  
|Condition après le démarrage de la méthode `reduceRight`|Élément passé à la fonction de rappel ?|  
|-----------------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant concatène les valeurs de tableau dans une chaîne en séparant les valeurs avec « :: ». Car aucune valeur initiale n’est fournie pour le `reduceRight` (méthode), le premier appel à la fonction de rappel a 456 comme le `previousValue` argument et 123 en tant que le `currentValue` argument.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant calcule la somme des carrés des éléments du tableau. Le `reduceRight` méthode est appelée avec une valeur initiale de 0.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient les éléments d’un tableau dont les valeurs sont compris entre 1 et 10. La valeur initiale de la `reduceRight` méthode est un tableau vide.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 La méthode `reduceRight` peut être appliquée à une chaîne. L’exemple suivant montre comment utiliser cette méthode pour inverser les caractères dans une chaîne.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md)