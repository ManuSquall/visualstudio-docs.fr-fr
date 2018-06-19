---
title: Promise.All, fonction (Promise) | Documents Microsoft
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639909"
---
# <a name="promiseall-function-promise"></a>Promise.all, fonction (Promise)
Joint plusieurs promesses et retourne une valeur uniquement quand toutes les promesses spécifiées ont été réalisées ou rejetées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `func1`  
 Obligatoire. Fonction qui retourne une promesse.  
  
 `func2`  
 Obligatoire. Fonction qui retourne une promesse.  
  
 `funcN`  
 Facultatif. Une ou plusieurs fonctions qui retournent une promesse.  
  
## <a name="remarks"></a>Remarques  
 Le résultat retourné est un tableau de valeurs retournées par les promesses réalisées. Si l'une des promesses jointes est rejetée, `Promise.all` en retourne immédiatement la raison (toutes les autres valeurs de retour sont ignorées).  
  
## <a name="example"></a>Exemple  
 Dans ce code, le premier appel au délai d'attente est retourné après 5 000 ms. Le gestionnaire d'achèvement appelle `Promise.all`, qui retourne une valeur uniquement quand les deux appels au délai d'attente sont réalisés ou rejetés.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)