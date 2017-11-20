---
title: "catch (méthode) (Promise) | Documents Microsoft"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="catch-method-promise"></a>catch, méthode (Promise)
Vous permet de spécifier le travail à effectuer sur le rejet d'une promesse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `promise`  
 Obligatoire. Objet de promesse.  
  
 `onRejected`  
 Obligatoire. Fonction de gestionnaire d'erreurs à exécuter quand une promesse est rejetée.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, le premier appel au délai d'attente est retourné après 5 000 ms. Dans ce code, la promesse est rejetée et la fonction de gestionnaire d'erreurs est exécutée.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]