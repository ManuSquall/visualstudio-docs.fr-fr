---
title: Array, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Array, objet (JavaScript)
Prend en charge la création de tableaux de tous types de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Array` est assigné.  
  
 `size`  
 Facultatif. Taille du tableau. Les tableaux étant en base zéro, les éléments créés auront des index allant de zéro jusqu'à `size` -1.  
  
 `element0,...,elementN`  
 Facultatif. Éléments à placer dans le tableau. Cette opération crée un tableau avec  *n*  + 1 éléments et un `length` de  *n*  + 1. Lorsque vous utilisez cette syntaxe, vous devez fournir plusieurs éléments.  
  
## <a name="remarks"></a>Remarques  
 Une fois le tableau créé, vous pouvez accéder à ses différents éléments en utilisant la notation [ ]. Notez que les tableaux en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sont de base zéro.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Vous pouvez passer un entier non signé 32 bits au constructeur `Array` pour spécifier la taille du tableau. Si la valeur est négative ou si elle n'est pas un entier, une erreur d'exécution se produit. Si vous exécutez le code suivant, vous devez voir cette erreur dans la console.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Si une seule valeur est passée au constructeur `Array` et qu'il ne s'agit pas d'un nombre, la propriété `length` a la valeur 1, et la valeur du seul élément devient l'unique argument passé.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Les tableaux JavaScript sont des tableaux creux, ce qui signifie que les éléments d'un tableau peuvent ne pas tous contenir des données. En JavaScript, seuls les éléments qui contiennent réellement des données figurent dans le tableau. Cela réduit la quantité de mémoire utilisée par le tableau.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Certains membres des listes suivantes ont été introduits dans les versions ultérieures. Pour plus d’informations, consultez [les informations de Version](../../javascript/reference/javascript-version-information.md) ou consultez la documentation pour les membres individuels.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Array`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-array.md)|Spécifie la fonction qui crée un tableau.|  
|[length, propriété (tableau)](../../javascript/reference/length-property-array-javascript.md)|Retourne une valeur entière correspondant à une unité de plus que l'indice d'élément le plus élevé d'un tableau.|  
|[prototype, propriété](../../javascript/reference/prototype-property-array.md)|Retourne une référence au prototype d'un tableau.|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant décrit les fonctions de l'objet `Array`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Array.From, fonction](../../javascript/reference/array-from-function-array-javascript.md)|Retourne un tableau à partir d'un objet de type tableau ou pouvant être itéré.|  
|[Fonction Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Retourne une valeur booléenne qui indique si un objet est un tableau.|  
|[Array.of, fonction](../../javascript/reference/array-of-function-array-javascript.md)|Retourne un tableau à partir des arguments transmis.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Array`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode concat (tableau)](../../javascript/reference/concat-method-array-javascript.md)|Retourne un nouveau tableau combinant deux tableaux.|  
|[Entries, méthode](../../javascript/reference/entries-method-array-javascript.md)|Retourne un itérateur qui contient les paires clé/valeur du tableau.|  
|[Méthode every](../../javascript/reference/every-method-array-javascript.md)|Vérifie si une fonction de rappel définie retourne `true` pour tous les éléments d'un tableau.|  
|[Fill, méthode](../../javascript/reference/fill-method-array-javascript.md)|Remplit un tableau avec une valeur spécifiée.|  
|[Méthode filter](../../javascript/reference/filter-method-array-javascript.md)|Appelle une fonction de rappel définie sur chaque élément d'un tableau et retourne un tableau de valeurs pour lesquelles la fonction de rappel retourne `true`.|  
|[findIndex (méthode)](../../javascript/reference/findindex-method-array-javascript.md)|Retourne une valeur d'index pour le premier élément du tableau qui répond aux critères de test spécifiés dans une fonction de rappel.|  
|[Méthode forEach](../../javascript/reference/foreach-method-array-javascript.md)|Appelle une fonction de rappel définie pour chaque élément d'un tableau.|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode indexOf (tableau)](../../javascript/reference/indexof-method-array-javascript.md)|Retourne l'index de la première occurrence d'une valeur dans un tableau.|  
|[isPrototypeOf, méthode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode join](../../javascript/reference/join-method-array-javascript.md)|Retourne un objet `String` formé de la concaténation de tous les éléments d'un tableau.|  
|[Keys, méthode](../../javascript/reference/keys-method-array-javascript.md)|Retourne un itérateur qui contient les valeurs d'index du tableau.|  
|[Méthode lastIndexOf (tableau)](../../javascript/reference/lastindexof-method-array-javascript.md)|Retourne l'index de la dernière occurrence d'une valeur spécifiée dans un tableau.|  
|[Méthode map](../../javascript/reference/map-method-array-javascript.md)|Appelle une fonction de rappel définie sur chaque élément d'un tableau et retourne un tableau contenant les résultats.|  
|[Méthode pop](../../javascript/reference/pop-method-array-javascript.md)|Supprime le dernier élément d'un tableau et le retourne.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne indiquant si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode push](../../javascript/reference/push-method-array-javascript.md)|Ajoute de nouveaux éléments à un tableau et retourne la nouvelle longueur du tableau.|  
|[Méthode reduce](../../javascript/reference/reduce-method-array-javascript.md)|Accumule un résultat unique en appelant une fonction de rappel définie pour tous les éléments d'un tableau. La valeur de retour de la fonction de rappel est le résultat accumulé, et est fournie en tant qu’argument dans le prochain appel à la fonction de rappel.|  
|[Méthode reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Accumule un résultat unique en appelant une fonction de rappel définie pour tous les éléments d'un tableau, dans l'ordre décroissant. La valeur de retour de la fonction de rappel est le résultat accumulé, et est fournie en tant qu’argument dans le prochain appel à la fonction de rappel.|  
|[Méthode reverse](../../javascript/reference/reverse-method-javascript.md)|Retourne un objet `Array` dans lequel les éléments sont inversés.|  
|[Méthode shift](../../javascript/reference/shift-method-array-javascript.md)|Supprime le premier élément d'un tableau et le retourne.|  
|[Méthode slice (tableau)](../../javascript/reference/slice-method-array-javascript.md)|Retourne une section d'un tableau.|  
|[Méthode some](../../javascript/reference/some-method-array-javascript.md)|Vérifie si une fonction de rappel définie retourne `true` pour tout élément d'un tableau.|  
|[Méthode sort](../../javascript/reference/sort-method-array-javascript.md)|Retourne un objet `Array` dans lequel les éléments sont triés.|  
|[Méthode splice](../../javascript/reference/splice-method-array-javascript.md)|Supprime les éléments d'un tableau et, si nécessaire, insère de nouveaux éléments à leur place, tout en retournant les éléments supprimés.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retourne une chaîne utilisant les paramètres régionaux.|  
|[ToString, méthode](../../javascript/reference/tostring-method-array.md)|Retourne une représentation d'un tableau sous forme de chaîne.|  
|[Méthode unshift](../../javascript/reference/unshift-method-array-javascript.md)|Insère de nouveaux éléments au début d'un tableau.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-array.md)|Obtient une référence au tableau.|  
|[Values, méthode](../../javascript/reference/values-method-array-javascript.md)|Retourne un itérateur qui contient les valeurs du tableau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)