---
title: "prototype, propriété (Boolean) | Documents Microsoft"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-boolean"></a>prototype, propriété (Boolean)
Retourne une référence au prototype pour un booléen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `boolean` est le nom d'un objet.  
  
 La propriété `prototype` fournit un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet. Les propriétés et les méthodes peuvent être ajoutées au prototype, mais un prototype différent ne peut pas être assigné aux objets incorporés.  
  
 Par exemple, pour ajouter une méthode à l'objet `Boolean` qui retourne la valeur de l'élément le plus volumineux du tableau, déclarez la fonction, ajoutez-la à `Boolean.prototype`, et réutilisez-la.  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]