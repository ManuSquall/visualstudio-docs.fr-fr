---
title: prototype, propriété (Error) | Documents Microsoft
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639479"
---
# <a name="prototype-property-error"></a>prototype, propriété (Error)
Retourne une référence au prototype pour une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `error` argument est le nom d’une erreur.  
  
 Utilisez le `prototype` propriété afin de fournir un ensemble de fonctionnalités de base à une erreur. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Error` qui retourne la valeur de l'élément le plus volumineux du tableau, déclarez la fonction, ajoutez-la à `Error.prototype`, et réutilisez-la.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets ont une `prototype` propriété est en lecture seule. Propriétés et méthodes peuvent être ajoutées au prototype, mais l’objet ne peut pas être assigné un prototype différent. Toutefois, les objets définis par l’utilisateur peuvent être affectés à un nouveau prototype.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]