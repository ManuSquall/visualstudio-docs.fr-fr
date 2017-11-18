---
title: "prototype, propriété (Date) | Documents Microsoft"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype, propriété (Date)
Retourne une référence au prototype pour une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `date` est le nom d'un objet.  
  
 Utilisez le `prototype` propriété afin de fournir un ensemble de fonctionnalités de base à une Date. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Date` qui retourne la valeur de l'élément le plus volumineux du tableau, déclarez la fonction, ajoutez-la à `Date.prototype`, et réutilisez-la.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets ont une `prototype` propriété est en lecture seule. Propriétés et méthodes peuvent être ajoutées au prototype, mais l’objet ne peut pas être assigné un prototype différent. Toutefois, les objets définis par l’utilisateur peuvent être affectés à un nouveau prototype.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]