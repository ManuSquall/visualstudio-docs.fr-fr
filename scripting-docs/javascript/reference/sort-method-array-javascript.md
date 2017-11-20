---
title: "Sort, méthode (Array) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
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
  
## <a name="remarks"></a>Remarques  
 Le `sort` méthode trie la `Array` objet sur place ; aucune nouvelle `Array` objet est créé lors de l’exécution.  
  
 Si vous fournissez une fonction dans le `sortFunction` argument, elle doit retourner une des valeurs suivantes :  
  
-   Une valeur négative si le premier argument passé est inférieur au deuxième argument.  
  
-   Zéro si les deux arguments sont équivalents.  
  
-   Une valeur positive si le premier argument est supérieur au deuxième argument.  
  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]