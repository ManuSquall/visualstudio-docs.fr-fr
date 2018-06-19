---
title: forEach, méthode (Set) (JavaScript) | Documents Microsoft
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636759"
---
# <a name="foreach-method-set-javascript"></a>forEach, méthode (Set) (JavaScript)
Exécute l’action spécifiée pour chaque élément dans un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `setObj`  
 Obligatoire. Objet `Set`.  
  
 `callbackfn`  
 Obligatoire. `callbackfn`accepte jusqu'à trois arguments. La fonction qui `forEach` appelle une fois pour chaque élément dans le jeu.  
  
 `thisArg`  
 Facultatif. Un objet qui le `this` mot clé peut faire référence au `callbackfn` (fonction). Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, key, setObj)`  
  
 Vous pouvez déclarer la fonction de rappel à l’aide de trois paramètres, comme indiqué dans le tableau suivant.  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`value`|Une valeur contenue dans le jeu.|  
|`key`|Une valeur contenue dans le jeu. Un ensemble ne comporte aucune clé, par conséquent, cette valeur est identique à `value`.|  
|`setObj`|Le `Set` objet à parcourir.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser `forEach`. Le `callbackfn` argument inclut le code pour la fonction de rappel.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre que vous pouvez également récupérer les membres d’un jeu en passant d’un seul paramètre à la fonction de rappel.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]