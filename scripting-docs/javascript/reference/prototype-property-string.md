---
title: "prototype, propriété (String) | Documents Microsoft"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>prototype, propriété (String)
Retourne une référence au prototype pour une classe de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `string` argument est le nom d’une chaîne.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à la `String` qui retourne la valeur du dernier élément de la chaîne de l’objet, déclarez la fonction, ajoutez-la à `String.prototype`, puis l’utiliser.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets ont une `prototype` propriété est en lecture seule. Propriétés et méthodes peuvent être ajoutées au prototype, mais l’objet ne peut pas être assigné un prototype différent. Toutefois, les objets définis par l’utilisateur peuvent être affectés à un nouveau prototype.  
  
 Les listes de méthodes et de propriétés pour chaque objet intrinsèque dans cette référence du langage indiquent ceux qui font partie de prototype de l’objet, et qui ne sont pas.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]