---
title: "chaque méthode (Array) (JavaScript) | Documents Microsoft"
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="every-method-array-javascript"></a>every, méthode (Array) (JavaScript)
Détermine si tous les membres d’un tableau remplissent le test spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Fonction acceptant jusqu'à trois arguments. Le `every` les appels de méthode le `callbackfn` fonction pour chaque élément dans `array1` jusqu'à ce que le `callbackfn` retourne `false`, ou jusqu'à la fin du tableau.|  
|`thisArg`|Facultatif. Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`. Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si le `callbackfn` fonction renvoie `true` pour tous les tableaux d’éléments ; sinon, `false`. Si le tableau est ne comporte aucun élément, le `every` méthode renvoie `true`.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `every` les appels de méthode le `callbackfn` fonction une fois pour chaque élément du tableau, dans l’index par ordre croissant, jusqu'à ce que le `callbackfn` fonction renvoie `false`. Si un élément qui provoque `callbackfn` pour retourner `false` est trouvée, le `every` méthode retourne immédiatement `false`. Dans le cas contraire, le `every` méthode renvoie `true`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `every` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
> [!NOTE]
>  Vous pouvez utiliser la [some, méthode (Array)](../../javascript/reference/some-method-array-javascript.md) pour vérifier si la fonction de rappel retourne `true` pour tout élément d’un tableau.  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, index, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec trois paramètres.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Paramètre de rappel|Définition|  
|------------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## <a name="modifying-the-array-object"></a>Modification de l'objet tableau  
 L'objet tableau peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `every`.  
  
|Condition après le démarrage de la méthode `every`|Élément passé à la fonction de rappel ?|  
|-----------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `every`.  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'argument `thisArg`, qui spécifie un objet auquel le mot clé `this` peut faire référence.  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Some, méthode (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Filter, méthode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)