---
title: "lastIndexOf, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), lastIndexOf (méthode)"
  - "lastIndexOf (méthode) (JavaScript)"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf, m&#233;thode (Array) (JavaScript)
Retourne l'index de la dernière occurrence d'une valeur spécifiée dans un tableau.  
  
## Syntaxe  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau à rechercher.|  
|`searchElement`|Obligatoire.  Valeur à trouver dans `array1`.|  
|`fromIndex`|Facultatif.  Index de tableau au niveau duquel commencer la recherche.  Si `fromIndex` est omis, la recherche démarre au niveau du dernier index du tableau.|  
  
## Valeur de retour  
 Index de la dernière occurrence de `searchElement` dans le tableau, ou \-1 si `searchElement` est introuvable.  
  
## Notes  
 La méthode `lastIndexOf` recherche une valeur spécifiée dans un tableau.  La méthode retourne l'index de la première occurrence, ou \-1 si la valeur spécifiée est introuvable.  
  
 La recherche est effectuée dans l'ordre d'indexation décroissant \(en commençant par le dernier membre\).  Pour effectuer la recherche dans l'ordre croissant, utilisez [indexOf, méthode \(Array\)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Les éléments du tableau sont comparés à la valeur `searchElement` pour déterminer leur égalité stricte, tout comme la comparaison effectuée par l'opérateur `===`.  Pour plus d'informations, consultez [Opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md).  
  
 L'argument `fromIndex` facultatif spécifie l'index du tableau au niveau duquel commencer la recherche.  Si `fromIndex` est supérieur ou égal à la longueur du tableau, la recherche porte sur l'intégralité du tableau.  Si `fromIndex` est négatif, la recherche commence à la longueur du tableau plus `fromIndex`.  Si l'index calculé est inférieur à 0, \-1 est retourné.  
  
## Exemple  
 Les exemples suivants illustrent l'utilisation de la méthode `lastIndexOf`.  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [indexOf, méthode \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)