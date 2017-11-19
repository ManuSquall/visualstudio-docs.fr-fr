---
title: "lastIndexOf, méthode (Array) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf, méthode (Array) (JavaScript)
Retourne l'index de la dernière occurrence d'une valeur spécifiée dans un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`array1`|Obligatoire. L’objet tableau à rechercher.|  
|`searchElement`|Obligatoire. La valeur à rechercher dans `array1`.|  
|`fromIndex`|Facultatif. L’index de tableau à partir duquel commencer la recherche. Si `fromIndex` est omis, la recherche commence au dernier index dans le tableau.|  
  
## <a name="return-value"></a>Valeur de retour  
 L’index de la dernière occurrence de `searchElement` dans le tableau, ou -1 si `searchElement` est introuvable.  
  
## <a name="remarks"></a>Remarques  
 Le `lastIndexOf` méthode recherche dans un tableau une valeur spécifiée. La méthode retourne l’index de la première occurrence, ou -1 si la valeur spécifiée est introuvable.  
  
 La recherche s’effectue dans l’ordre d’index décroissant (le dernier membre tout d’abord). Pour rechercher dans l’ordre croissant, utilisez le [IndexOf, méthode (Array)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Les éléments du tableau sont comparées à la `searchElement` valeur d’identité, similaire à la comparaison effectuée par le `===` opérateur. Pour plus d’informations, consultez [opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md).  
  
 Le paramètre facultatif `fromIndex` argument spécifie l’index de tableau à partir duquel commencer la recherche. Si `fromIndex` est supérieur ou égal à la longueur du tableau, la totalité du tableau est recherché. Si `fromIndex` est négatif, la recherche commence à la longueur du tableau plue `fromIndex`. Si l’index calculée est inférieur à 0, -1 est retourné.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent l’utilisation de la `lastIndexOf` (méthode).  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode indexOf (tableau)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)