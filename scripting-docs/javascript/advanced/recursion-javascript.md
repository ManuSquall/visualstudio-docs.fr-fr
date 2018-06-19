---
title: Récursivité (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- functions, recursive function calls
- recursive procedures
- function calls, recursive
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06735c244ed6bd3c8d9abe59123f9f961e6f1847
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568889"
---
# <a name="recursion-javascript"></a>Récursivité (JavaScript)
La récursivité est une technique de programmation importante, dans laquelle une fonction s’appelle elle-même.  
  
## <a name="an-example-of-recursion"></a>Exemple de récursivité  
 Le calcul de factorielles constitue un bon exemple. La factorielle d’un nombre *n* est calculée en multipliant 1 \* 2 \* 3 \*... *n*. L’exemple suivant montre comment calculer des factorielles de manière itérative, c’est-à-dire en utilisant une boucle `while` dans laquelle le résultat est calculé.  
  
```JavaScript  
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
  
 Il est très facile de rendre l’exemple récursif. Au lieu d’utiliser une boucle `while` pour calculer la valeur, il suffit de rappeler `factorial` en passant la valeur la plus faible suivante. La récursivité s’arrête quand la valeur est 1.  
  
```JavaScript  
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