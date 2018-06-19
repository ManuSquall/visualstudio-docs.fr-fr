---
title: prototype, propriété (Array) | Documents Microsoft
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639009"
---
# <a name="prototype-property-array"></a>prototype, propriété (Array)
Retourne une référence au prototype pour une classe de tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `array` argument est le nom d’un tableau.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Array` qui retourne la valeur de l'élément le plus volumineux du tableau, déclarez la fonction, ajoutez-la à `Array.prototype`, et réutilisez-la.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets ont une `prototype` propriété est en lecture seule. Propriétés et méthodes peuvent être ajoutées au prototype, mais l’objet ne peut pas être assigné un prototype différent. Toutefois, les objets définis par l’utilisateur peuvent être affectés à un nouveau prototype.  
  
 Les listes de méthodes et de propriétés pour chaque objet intrinsèque dans cette référence du langage indiquent ceux qui font partie de prototype de l’objet, et qui ne sont pas.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]