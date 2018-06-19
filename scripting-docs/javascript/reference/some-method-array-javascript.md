---
title: Some, méthode (Array) (JavaScript) | Documents Microsoft
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641759"
---
# <a name="some-method-array-javascript"></a>some, méthode (Array) (JavaScript)
Détermine si la fonction de rappel spécifiée retourne `true` pour tout élément d’un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`callbackfn`|Obligatoire. Fonction acceptant jusqu'à trois arguments. Le `some` les appels de méthode le `callbackfn` fonction pour chaque élément dans `array1` jusqu'à ce que le `callbackfn` retourne `true`, ou jusqu'à la fin du tableau.|  
|`thisArg`|Facultatif. Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`. Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si le `callbackfn` fonction renvoie `true` pour n’importe quel élément du tableau ; sinon, `false`.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `some` les appels de méthode le `callbackfn` fonction sur chaque élément du tableau, dans l’index par ordre croissant, jusqu'à ce que le `callbackfn` fonction renvoie `true`. Si un élément qui provoque `callbackfn` pour retourner `true` est trouvée, le `some` méthode retourne immédiatement `true`. Si le rappel ne renvoie pas `true` sur n’importe quel élément, le `some` méthode renvoie `false`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `some` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
> [!NOTE]
>  Vous pouvez utiliser la [every, méthode (Array)](../../javascript/reference/every-method-array-javascript.md) pour vérifier si la fonction de rappel retourne `true` pour tous les éléments d’un tableau.  
  
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
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `some`.  
  
|Condition après le démarrage de la méthode `some`|Élément passé à la fonction de rappel ?|  
|----------------------------------------------|------------------------------------------|  
|L'élément est ajouté au-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `some` méthode pour déterminer si tous les éléments dans un tableau sont pairs.  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `thisArg` paramètre qui spécifie un objet auquel le `this` mot clé peut faire référence. Il vérifie si un des nombres dans un tableau sont en dehors de la plage fournie par un objet passé  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [chaque méthode (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [Filter, méthode (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Méthode map (Array)](../../javascript/reference/map-method-array-javascript.md)