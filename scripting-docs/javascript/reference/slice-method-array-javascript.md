---
title: "slice, méthode (Array) (JavaScript) | Documents Microsoft"
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice, méthode (Array) (JavaScript)
Retourne une section d'un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet `Array`.  
  
 `start`  
 Obligatoire. Début de la partie spécifiée des `arrayObj`.  
  
 `end`  
 Facultatif. La fin de la partie spécifiée des `arrayObj`.  
  
## <a name="remarks"></a>Remarques  
 Le `slice` méthode retourne un `Array` objet contenant la partie spécifiée des `arrayObj`.  
  
 Le `slice` méthode copie les, mais sans inclure l’élément indiqué par `end`. Si `start` est négatif, il est traité comme `length`  +  `start`, où `length` est la longueur du tableau. Si `end` est négatif, il est traité comme `length`  +  `end` où `length` est la longueur du tableau. Si `end` est omis, l'extraction continue jusqu'à la fin de `arrayObj`. Si `end` se produit avant `start`, sans les éléments sont copiés dans le nouveau tableau.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser la méthode `slice`. Dans le premier exemple, tous les dossiers sauf le dernier élément de `myArray` est copié dans `newArray`. Dans le deuxième exemple, uniquement les deux derniers éléments de `myArray` sont copiés dans `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [slice, méthode (String)](../../javascript/reference/slice-method-string-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)