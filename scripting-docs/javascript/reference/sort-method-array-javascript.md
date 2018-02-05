---
title: "Sort, méthode (Array) (JavaScript) | Documents Microsoft"
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2018
---
# <a name="sort-method-array-javascript"></a>sort, méthode (Array) (JavaScript)
Trie une `Array`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Tout objet `Array`.  
  
 `sortFunction`  
 Facultatif. Le nom de la fonction utilisée pour déterminer l’ordre des éléments. Si omis, les éléments sont triés par ordre croissant, ordre des caractères ASCII.  
  
## <a name="return-value"></a>Valeur de retour  
 Le tableau trié.  
  
## <a name="remarks"></a>Notes  
 Le `sort` méthode trie la `Array` objet sur place ; aucune nouvelle `Array` objet est créé lors de l’exécution.  
  
 `sortFunction`accepte deux arguments et doit retourner l’une des valeurs suivantes :  
  
-   Une valeur négative (inférieur à 0) si le premier argument passé est inférieur au second.  Le premier argument est trié à un index de niveau inférieur.
  
-   Zéro (0) si les deux arguments sont équivalents.  Les deux arguments sont triés par rapport à d’autres éléments du tableau, mais ne sont pas triées par rapport à l’autre.
  
-   Une valeur positive (supérieure à 0) si le premier argument est supérieur au deuxième argument.  Le deuxième argument est trié à un index de niveau inférieur.
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `sort`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]