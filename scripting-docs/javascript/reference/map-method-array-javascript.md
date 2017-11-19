---
title: "Map, méthode (Array) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>map, méthode (Array) (JavaScript)
Appelle une fonction de rappel définie sur chaque élément d'un tableau et retourne un tableau contenant les résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Fonction acceptant jusqu'à trois arguments. La méthode `map` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`thisArg`|Facultatif. Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`. Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau dans lequel chaque élément est la valeur de retour de la fonction de rappel pour l'élément de tableau d'origine associé.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 La méthode `map` appelle la fonction `callbackfn` une fois pour chaque élément du tableau, dans l'ordre d'indexation croissant. La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `map` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
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
 L'objet tableau peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `map`.  
  
|Condition après le démarrage de la méthode `map`|Élément passé à la fonction de rappel ?|  
|---------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `map`.  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'argument `thisArg`, qui spécifie un objet auquel le mot clé `this` peut faire référence.  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, une méthode [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intégrée est utilisée comme fonction de rappel.  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>Exemple  
 La méthode `map` peut être appliquée à une chaîne. L'exemple suivant illustre ce comportement.  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)   
 [Filter, méthode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach, méthode (Array)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Hilo JavaScript exemple d’application (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)