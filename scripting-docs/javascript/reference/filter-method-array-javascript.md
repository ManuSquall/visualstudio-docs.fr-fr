---
title: Filter, méthode (Array) (JavaScript) | Documents Microsoft
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
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637779"
---
# <a name="filter-method-array-javascript"></a>filter, méthode (Array) (JavaScript)
Retourne les éléments d’un tableau qui répondent à la condition spécifiée dans une fonction de rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Fonction acceptant jusqu'à trois arguments. La méthode `filter` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`thisArg`|Facultatif. Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`. Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## <a name="return-value"></a>Valeur de retour  
 Un nouveau tableau qui contient toutes les valeurs pour lesquelles la fonction de rappel retourne `true`. Si la fonction de rappel retourne `false` pour tous les éléments de `array1`, la longueur du nouveau tableau est 0.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 La méthode `filter` appelle la fonction `callbackfn` une fois pour chaque élément du tableau, dans l'ordre d'indexation croissant. La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `filter` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, index, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec trois paramètres maximum.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## <a name="modifying-the-array-object"></a>Modification de l'objet tableau  
 La méthode `filter` ne modifie pas directement le tableau d'origine, mais la fonction de rappel peut le modifier. Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `filter`.  
  
|Condition après le démarrage de la méthode `filter`|Élément passé à la fonction de rappel ?|  
|------------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `filter`.  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, l'argument `callbackfn` inclut le code de la fonction de rappel.  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les noms des propriétés qui commencent par la lettre « css » dans la `window` objet DOM.  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'argument `thisArg`, qui spécifie un objet auquel le mot clé `this` peut faire référence.  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>Exemple  
 Le `filter` méthode peut être appliquée à une chaîne au lieu d’un tableau. L'exemple suivant montre comment effectuer cette opération.  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)   
 [Map, méthode (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [Méthode forEach (Array)](../../javascript/reference/foreach-method-array-javascript.md)