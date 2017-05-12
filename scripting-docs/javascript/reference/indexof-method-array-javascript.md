---
title: "indexOf, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript), indexOf (méthode)"
  - "indexOf (méthode) (JavaScript)"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf, m&#233;thode (Array) (JavaScript)
Retourne l'index de la première occurrence d'une valeur dans un tableau.  
  
## Syntaxe  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire.  Objet tableau.|  
|`searchElement`|Obligatoire.  Valeur à trouver dans `array1`.|  
|`fromIndex`|Facultatif.  Index de tableau au niveau duquel commencer la recherche.  Si `fromIndex` est omis, la recherche démarre à l'index 0.|  
  
## Valeur de retour  
 Index de la première occurrence de `searchElement` dans le tableau, ou \-1 si `searchElement` est introuvable.  
  
## Notes  
 La méthode `indexOf` recherche une valeur spécifiée dans un tableau.  La méthode retourne l'index de la première occurrence, ou \-1 si la valeur spécifiée est introuvable.  
  
 La recherche est effectuée dans l'ordre d'indexation croissant.  
  
 Les éléments du tableau sont comparés à la valeur `searchElement` pour déterminer leur égalité stricte, comme avec l'opérateur `===`.  Pour plus d'informations, consultez [Opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md).  
  
 L'argument `fromIndex` facultatif spécifie l'index du tableau au niveau duquel commencer la recherche.  Si `fromIndex` est supérieur ou égal à la longueur du tableau, \-1 est retourné.  Si `fromIndex` est négatif, la recherche commence à la longueur du tableau plus `fromIndex`.  
  
## Exemple  
 Les exemples suivants illustrent l'utilisation de la méthode `indexOf`.  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)