---
title: Promise.Reject, fonction (Promise) | Documents Microsoft
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639269"
---
# <a name="promisereject-function-promise"></a>Promise.reject, fonction (Promise)
Crée une promesse rejetée avec un résultat égal à l’argument transmis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `r`  
 Obligatoire. Motif de rejet de la promesse.  
  
## <a name="remarks"></a>Remarques  
 La fonction de gestion d'erreurs de la méthode `then` ou `catch` s'exécute quand la promesse rejetée est retournée.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)