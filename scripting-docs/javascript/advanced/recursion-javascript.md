---
title: "R&#233;cursivit&#233; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fonctions, appels de fonction récursive"
  - "procédures récursives"
  - "appels de fonction, récursive"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# R&#233;cursivit&#233; (JavaScript)
La récursivité est une technique de programmation importante dans laquelle une fonction s'appelle elle\-même.  
  
## Exemple de récursivité  
 Le calcul de factorielles constitue un exemple de récursivité.  La factorielle d'un nombre *n* est calculée en multipliant 1 x 2 x 3 x...  *n*.  L'exemple suivant montre comment calculer des factorielles de manière itérative, autrement dit, à l'aide d'une boucle `while` dans laquelle le résultat est calculé.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Vous pouvez très simplement rendre l'exemple récursif.  Au lieu d'utiliser une boucle `while` pour calculer la valeur, vous pouvez simplement appeler `factorial` à nouveau, en passant la valeur suivante la plus faible.  La récursivité s'arrête lorsque la valeur est 1.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```