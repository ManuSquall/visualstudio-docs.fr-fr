---
title: "Array, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Array"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array (objet)"
  - "constructor (propriété)"
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Array, objet (JavaScript)
Prend en charge la création de tableaux de tout type de données.  
  
## Syntaxe  
  
```  
  
        arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Nom de la variable à laquelle l'objet `Array` est assigné.  
  
 `size`  
 Facultatif.  Taille du tableau.  Comme les tableaux sont de base zéro, les éléments créés ont des index entre zéro et `size` \-1.  
  
 `element0,...,elementN`  
 Facultatif.  Éléments à placer dans le tableau.  Cet argument crée un tableau avec *n* \+ 1 éléments et une propriété `length` de *n* \+ 1.  Avec cette syntaxe, vous devez fournir plusieurs éléments.  
  
## Notes  
 Après la création d'un tableau, vous pouvez accéder à des éléments individuels du tableau en utilisant la notation \[\].  Notez que les tableaux dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sont de base zéro.  
  
```javascript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Vous pouvez passer un entier 32 bits non signé au constructeur `Array` pour spécifier la taille du tableau.  Si la valeur est négative ou n'est pas un entier, une erreur d'exécution se produit.  Si vous exécutez le code suivant, vous devez voir cette erreur dans la console.  
  
```javascript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Si une seule valeur est passée au constructeur `Array` et qu'il ne s'agit pas d'un nombre, la propriété `length` a la valeur 1 et la valeur du seul élément devient l'unique argument transmis.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Les tableaux JavaScript sont des tableaux partiellement alloués, ce qui signifie que les éléments dans un tableau ne peuvent pas tous contenir des données.  Dans JavaScript, seuls les éléments qui contiennent réellement des données figurent dans le tableau.  Cela réduit la quantité de mémoire utilisée par le tableau.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Certains membres des listes suivantes ont été introduits dans les versions ultérieures.  Pour plus d'informations, consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md) ou la documentation relative aux différents membres.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Array`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété constructor](../../javascript/reference/constructor-property-array.md)|Spécifie la fonction qui crée un tableau.|  
|[Propriété length \(Array\)](../../javascript/reference/length-property-array-javascript.md)|Retourne une valeur entière correspondant à une unité de plus que l'indice d'élément le plus élevé d'un tableau.|  
|[Propriété prototype](../../javascript/reference/prototype-property-array.md)|Retourne une référence au prototype d'un tableau.|  
  
## Fonctions  
 Le tableau suivant décrit les fonctions de l'objet `Array`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction Array.from](../../javascript/reference/array-from-function-array-javascript.md)|Retourne un tableau à partir d'un objet de type tableau ou pouvant être itéré.|  
|[Fonction Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Retourne une valeur booléenne qui indique si un objet est un tableau.|  
|[Fonction Array.of](../../javascript/reference/array-of-function-array-javascript.md)|Retourne un tableau à partir des arguments transmis.|  
  
<a name="js56jsobjarraymeth"></a>   
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Array`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode concat \(Array\)](../../javascript/reference/concat-method-array-javascript.md)|Retourne un nouveau tableau combinant deux tableaux.|  
|[Méthode entries](../../javascript/reference/entries-method-array-javascript.md)|Retourne un itérateur qui contient les paires clé\/valeur du tableau.|  
|[Méthode every](../../javascript/reference/every-method-array-javascript.md)|Vérifie si une fonction de rappel définie retourne `true` pour tous les éléments d'un tableau.|  
|[Méthode fill](../../javascript/reference/fill-method-array-javascript.md)|Remplit un tableau avec une valeur spécifiée.|  
|[Méthode filter](../../javascript/reference/filter-method-array-javascript.md)|Appelle une fonction de rappel définie sur chaque élément d'un tableau et retourne un tableau de valeurs pour lesquelles la fonction de rappel retourne `true`.|  
|[Méthode findIndex](../../javascript/reference/findindex-method-array-javascript.md)|Retourne une valeur d'index pour le premier élément du tableau qui répond aux critères de test spécifiés dans une fonction de rappel.|  
|[Méthode forEach](../../javascript/reference/foreach-method-array-javascript.md)|Appelle une fonction de rappel définie pour chaque élément d'un tableau.|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode indexOf \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)|Retourne l'index de la première occurrence d'une valeur dans un tableau.|  
|[Méthode isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode join](../../javascript/reference/join-method-array-javascript.md)|Retourne un objet `String` formé de la concaténation de tous les éléments d'un tableau.|  
|[Méthode keys](../../javascript/reference/keys-method-array-javascript.md)|Retourne un itérateur qui contient les valeurs d'index du tableau.|  
|[Méthode lastIndexOf \(Array\)](../../javascript/reference/lastindexof-method-array-javascript.md)|Retourne l'index de la dernière occurrence d'une valeur spécifiée dans un tableau.|  
|[Méthode map](../../javascript/reference/map-method-array-javascript.md)|Appelle une fonction de rappel définie sur chaque élément d'un tableau et retourne un tableau contenant les résultats.|  
|[Méthode pop](../../javascript/reference/pop-method-array-javascript.md)|Supprime le dernier élément d'un tableau et le retourne.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne qui indique si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode push](../../javascript/reference/push-method-array-javascript.md)|Ajoute de nouveaux éléments à un tableau et retourne la nouvelle longueur du tableau.|  
|[Méthode reduce](../../javascript/reference/reduce-method-array-javascript.md)|Accumule un résultat unique en appelant une fonction de rappel définie pour tous les éléments d'un tableau.  La valeur de retour de la fonction de rappel est le résultat accumulé et est fournie comme argument dans l'appel suivant à la fonction de rappel.|  
|[Méthode reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Accumule un résultat unique en appelant une fonction de rappel définie pour tous les éléments d'un tableau, dans l'ordre décroissant.  La valeur de retour de la fonction de rappel est le résultat accumulé et est fournie comme argument dans l'appel suivant à la fonction de rappel.|  
|[Méthode reverse](../../javascript/reference/reverse-method-javascript.md)|Retourne un objet `Array` dans lequel les éléments sont inversés.|  
|[Méthode shift](../../javascript/reference/shift-method-array-javascript.md)|Supprime le premier élément d'un tableau et le retourne.|  
|[Méthode slice \(Array\)](../../javascript/reference/slice-method-array-javascript.md)|Retourne une section d'un tableau.|  
|[Méthode some](../../javascript/reference/some-method-array-javascript.md)|Vérifie si une fonction de rappel définie retourne `true` pour tout élément d'un tableau.|  
|[Méthode sort](../../javascript/reference/sort-method-array-javascript.md)|Retourne un objet `Array` dans lequel les éléments sont triés.|  
|[Méthode splice](../../javascript/reference/splice-method-array-javascript.md)|Supprime les éléments d'un tableau et, si nécessaire, insère de nouveaux éléments à leur place, tout en retournant les éléments supprimés.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retourne une chaîne utilisant les paramètres régionaux actuels.|  
|[Méthode toString](../../javascript/reference/tostring-method-array.md)|Retourne une représentation sous forme de chaîne d'un tableau.|  
|[Méthode unshift](../../javascript/reference/unshift-method-array-javascript.md)|Insère de nouveaux éléments au début d'un tableau.|  
|[Méthode valueOf](../../javascript/reference/valueof-method-array.md)|Obtient une référence au tableau.|  
|[Méthode values](../../javascript/reference/values-method-array-javascript.md)|Retourne un itérateur qui contient les valeurs du tableau.|  
  
## Voir aussi  
 [Exemple d'application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)