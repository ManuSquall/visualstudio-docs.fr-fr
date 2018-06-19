---
title: POP, méthode (Array) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639279"
---
# <a name="pop-method-array-javascript"></a>pop, méthode (Array) (JavaScript)
Supprime le dernier élément d'un tableau et le retourne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>Remarques  
 Le [push](../../javascript/reference/push-method-array-javascript.md) et `pop` méthodes permettent de simuler une pile, qui utilise le principe du dernier entré, premier sorti (LIFO) pour stocker les données.  
  
 Requis `arrayObj` référence est un `Array` objet.  
  
 Si le tableau est vide, `undefined` est retourné.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `pop`.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode push (Array)](../../javascript/reference/push-method-array-javascript.md)