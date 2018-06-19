---
title: forEach, méthode (Array) (JavaScript) | Documents Microsoft
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637489"
---
# <a name="foreach-method-array-javascript"></a>forEach, méthode (Array) (JavaScript)
Exécute l'action spécifiée pour chaque élément d'un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Fonction acceptant jusqu'à trois arguments. La méthode `forEach` appelle la fonction `callbackfn` une fois pour chaque élément du tableau.|  
|`thisArg`|Facultatif. Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`. Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 La méthode `forEach` appelle la fonction `callbackfn` une fois pour chaque élément présent dans le tableau, dans l'ordre d'indexation croissant. La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `forEach` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, index, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec trois paramètres maximum.  
  
 Les paramètres de la fonction de rappel sont les suivants :  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## <a name="modifying-the-array-object"></a>Modification de l'objet tableau  
 La méthode `forEach` ne modifie pas directement le tableau d'origine, mais la fonction de rappel peut le modifier. Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `forEach`.  
  
|Condition après le démarrage de la méthode `forEach`|Élément passé à la fonction de rappel ?|  
|---------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre l'utilisation de la méthode `forEach`.  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, l'argument `callbackfn` inclut le code de la fonction de rappel.  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'argument `thisArg`, qui spécifie un objet désigné par le mot clé `this`.  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Filter, méthode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Map, méthode (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [Some, méthode (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)   
 [Hilo JavaScript exemple d’application (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)