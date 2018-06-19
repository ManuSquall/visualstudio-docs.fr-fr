---
title: prototype, propriété (Number) | Documents Microsoft
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639229"
---
# <a name="prototype-property-number"></a>prototype, propriété (Number)
Retourne une référence au prototype pour une classe de nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `number` argument est le nom d’un nombre.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à la `Number` qui retourne les chiffres de (entier) de l’objet, déclarez la fonction, ajoutez-la à `Number.prototype`, puis l’utiliser.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets ont une `prototype` propriété est en lecture seule. Propriétés et méthodes peuvent être ajoutées au prototype, mais l’objet ne peut pas être assigné un prototype différent. Toutefois, les objets définis par l’utilisateur peuvent être affectés à un nouveau prototype.  
  
 Les listes de méthodes et de propriétés pour chaque objet intrinsèque dans cette référence du langage indiquent ceux qui font partie de prototype de l’objet, et qui ne sont pas.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]