---
title: "every, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), every (méthode)"
  - "every (méthode)"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every, m&#233;thode (Array) (JavaScript)
Détermine si tous les membres d'un tableau répondent aux besoins du test spécifié.  
  
## Syntaxe  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau.|  
|`callbackfn`|Obligatoire.  Fonction qui accepte jusqu'à trois arguments.  La méthode `every` appelle la fonction `callbackfn` pour chaque élément de `array1` jusqu'à ce que la fonction `callbackfn` retourne la valeur `false`, ou jusqu'à la fin du tableau.|  
|`thisArg`|Facultatif.  Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`.  Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## Valeur de retour  
 `true` si la fonction `callbackfn` retourne la valeur `true` pour tous les éléments du tableau ; sinon, `false`.  Si le tableau ne contient aucun élément, la méthode `every` retourne `true`.  
  
## Exceptions  
 Si l'argument `callbackfn`, n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## Notes  
 La méthode `every` appelle la fonction `callbackfn` une fois pour chaque élément de tableau, dans l'ordre d'index croissant, jusqu'à ce que la fonction `callbackfn` retourne la valeur `false`.  Si un élément qui fait que la fonction `callbackfn` retourne la valeur `false` est trouvé, la méthode `every` retourne immédiatement la valeur `false`.  Sinon, la méthode `every` retourne `true`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `every` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
> [!NOTE]
>  Vous pouvez utiliser la [some, méthode \(Array\)](../../javascript/reference/some-method-array-javascript.md) pour vérifier si la fonction de rappel retourne la valeur `true` pour tous les éléments d'un tableau.  
  
## Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, index, array1)`  
  
 Vous pouvez déclarer la fonction de rappel avec jusqu'à trois paramètres.  
  
 Le tableau suivant répertorie les paramètres de la fonction de rappel.  
  
|Paramètre de rappel|Définition|  
|-------------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`array1`|Objet de tableau qui contient l'élément.|  
  
## Modification de l'objet tableau  
 L'objet tableau ne peut être modifié par la fonction de rappel.  
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `every`.  
  
|Condition après le démarrage de la méthode `every`|Élément passé à la fonction de rappel ?|  
|--------------------------------------------------------|---------------------------------------------|  
|L'élément est ajouté au\-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `every`.  
  
```javascript  
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
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'argument `thisArg`, qui spécifie un objet auquel le mot clé `this` peut faire référence.  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [some, méthode \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter, méthode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)