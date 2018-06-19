---
title: IndexOf, méthode (Array) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637479"
---
# <a name="indexof-method-array-javascript"></a>indexOf, méthode (Array) (JavaScript)
Retourne l'index de la première occurrence d'une valeur dans un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. Un objet tableau.|  
|`searchElement`|Obligatoire. La valeur à rechercher dans `array1`.|  
|`fromIndex`|Facultatif. L’index de tableau à partir duquel commencer la recherche. Si `fromIndex` est omis, la recherche commence à l’index 0.|  
  
## <a name="return-value"></a>Valeur de retour  
 L’index de la première occurrence de `searchElement` dans le tableau, ou -1 si `searchElement` est introuvable.  
  
## <a name="remarks"></a>Remarques  
 Le `indexOf` méthode recherche dans un tableau une valeur spécifiée. La méthode retourne l’index de la première occurrence, ou -1 si la valeur spécifiée est introuvable.  
  
 La recherche s’effectue dans l’ordre d’index croissant.  
  
 Les éléments du tableau sont comparées à la `searchElement` valeur d’identité, similaire à la `===` opérateur. Pour plus d’informations, consultez [opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md).  
  
 Le paramètre facultatif `fromIndex` argument spécifie l’index de tableau à partir duquel commencer la recherche. Si `fromIndex` est supérieur ou égal à la longueur du tableau, -1 est retourné. Si `fromIndex` est négatif, la recherche commence à la longueur du tableau plue `fromIndex`.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent l’utilisation de la `indexOf` (méthode).  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)