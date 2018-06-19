---
title: push, méthode (Array) (JavaScript) | Documents Microsoft
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639449"
---
# <a name="push-method-array-javascript"></a>push, méthode (Array) (JavaScript)
Ajoute de nouveaux éléments à un tableau et retourne la nouvelle longueur du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet `Array`.  
  
 `item, item2,. . ., itemN`  
 Facultatif. Nouveaux éléments de la `Array`.  
  
## <a name="remarks"></a>Remarques  
 Le `push` et `pop` méthodes vous permettent de simuler une dernier entré, premier sorti de pile.  
  
 Le `push` méthode ajoute les éléments dans l’ordre dans lequel ils apparaissent. Si l’un des arguments est un tableau, il est ajouté en tant qu’un seul élément. Utilisez la `concat` méthode pour joindre les éléments à partir de deux ou plusieurs tableaux.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `push`.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode concat (tableau)](../../javascript/reference/concat-method-array-javascript.md)   
 [Méthode pop (Array)](../../javascript/reference/pop-method-array-javascript.md)