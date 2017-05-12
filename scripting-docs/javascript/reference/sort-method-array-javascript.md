---
title: "sort, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort (méthode)"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort, m&#233;thode (Array) (JavaScript)
Trie un `Array`.  
  
## Syntaxe  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Paramètres  
 `arrayObj`  
 Requis.  Tout objet `Array`.  
  
 `sortFunction`  
 Optionnel.  Nom de la fonction employée pour déterminer l'ordre des éléments.  Si omise, les éléments sont triés en ordre croissant de caractères ASCII.  
  
## Valeur de retour  
 Tableau trié.  
  
## Notes  
 La méthode `sort` trie l'objet `Array` existant. Aucun nouvel objet `Array` n'est créé pendant l'exécution.  
  
 Si vous indiquez une fonction dans l'argument `sortFunction`, elle doit retourner l'une des valeurs suivantes :  
  
-   Une valeur négative si le premier argument passé est inférieur au deuxième argument.  
  
-   La valeur zéro si les deux arguments sont équivalents.  
  
-   Une valeur positive si le premier argument est supérieur au deuxième argument.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `sort`.  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]