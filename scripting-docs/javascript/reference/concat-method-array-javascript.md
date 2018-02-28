---
title: "concat, méthode (Array) (JavaScript) | Documents Microsoft"
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat, méthode (Array) (JavaScript)
Combine deux ou plusieurs tableaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `array1`  
 Obligatoire. Le `Array` de l’objet pour lequel d’autres tableaux est concaténés.  
  
 `item1,. . ., itemN`  
 Facultatif. Éléments supplémentaires à ajouter à la fin de `array1`.  
  
## <a name="remarks"></a>Remarques  
 Le `concat` méthode retourne un `Array` objet contenant la concaténation de `array1` et tous les autres éléments fournis.  
  
 Les éléments à ajouter (*item1 itemN*) dans le tableau sont insérés dans l’ordre, à partir du premier élément dans la liste. Si l’un des éléments est un tableau, son contenu est ajouté à la fin de `array1`. Si l’élément n’est pas un tableau, il est ajouté à la fin du tableau en tant qu’un seul élément du tableau.  
  
 Éléments des tableaux sources sont copiés dans le tableau obtenu comme suit :  
  
-   Si un objet est copié à partir des concaténation dans le nouveau tableau de tableaux, la référence d’objet continue de pointer vers le même objet. Une modification dans le nouveau tableau ou tableau d’origine entraîne une modification à l’autre.  
  
-   Si une valeur de nombre ou une chaîne est ajoutée dans le nouveau tableau, seule la valeur est copiée. Modification de la valeur dans un tableau n’affecte pas la valeur de l’autre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la `concat` méthode avec un tableau :  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [concat, méthode (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [Méthode join (Array)](../../javascript/reference/join-method-array-javascript.md)