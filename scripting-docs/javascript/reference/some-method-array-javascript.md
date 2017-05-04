---
title: "some, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), some (méthode)"
  - "some (méthode) (JavaScript)"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some, m&#233;thode (Array) (JavaScript)
Détermine si la fonction de rappel spécifiée retourne la valeur `true` pour tout élément d'un tableau.  
  
## Syntaxe  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau.|  
|`callbackfn`|Obligatoire.  Fonction qui accepte jusqu'à trois arguments.  La méthode `some` appelle la fonction `callbackfn` pour chaque élément de `array1` jusqu'à ce que la fonction `callbackfn` retourne la valeur `true`, ou jusqu'à la fin du tableau.|  
|`thisArg`|Facultatif.  Objet auquel le mot clé `this` peut faire référence dans la fonction `callbackfn`.  Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.|  
  
## Valeur de retour  
 `true` si la fonction `callbackfn` retourne la valeur `true` pour tout élément du tableau ; sinon, `false`.  
  
## Exceptions  
 Si l'argument `callbackfn`, n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## Notes  
 La méthode `some` appelle la fonction `callbackfn` sur chaque élément de tableau, dans l'ordre croissante d'index, jusqu'à ce que la fonction `callbackfn` retourne la valeur `true`.  Si un élément qui fait que la fonction `callbackfn` retourne la valeur `true` est trouvé, la méthode `some` retourne immédiatement la valeur `true`.  Si le rappel ne retourne pas la valeur `true` sur un élément, la méthode `some` retourne la valeur `false`.  
  
 La fonction de rappel n'est pas appelée pour les éléments manquants du tableau.  
  
 Outre les objets tableau, la méthode `some` peut être utilisée par tout objet comportant une propriété `length` et des noms de propriété indexés de manière numérique.  
  
> [!NOTE]
>  Vous pouvez utiliser la [every, méthode \(Array\)](../../javascript/reference/every-method-array-javascript.md) pour vérifier si la fonction de rappel retourne la valeur `true` pour tous les éléments d'un tableau.  
  
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
  
 Le tableau suivant décrit les résultats de la modification de l'objet tableau après le démarrage de la méthode `some`.  
  
|Condition après le démarrage de la méthode `some`|Élément passé à la fonction de rappel ?|  
|-------------------------------------------------------|---------------------------------------------|  
|L'élément est ajouté au\-delà de la longueur d'origine du tableau.|Non.|  
|L'élément est ajouté pour compléter un élément manquant du tableau.|Oui, si cet index n'a pas encore été passé à la fonction de rappel.|  
|L'élément est modifié.|Oui, si cet élément n'a pas encore été passé à la fonction de rappel.|  
|L'élément est supprimé du tableau.|Non, sauf si cet élément a déjà été passé à la fonction de rappel.|  
  
## Exemple  
 L'exemple suivant utilise la méthode `some` pour déterminer si les éléments d'un tableau sont égaux.  
  
```javascript  
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
  
## Exemple  
 L'exemple suivant indique comment utiliser le paramètre `thisArg`, qui spécifie un objet auquel le mot clé `this` peut faire référence.  Il vérifie si l'un des nombres dans un tableau se trouve en dehors de la plage fournie par un objet passé  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [every, méthode \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter, méthode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map, méthode \(Array\)](../../javascript/reference/map-method-array-javascript.md)