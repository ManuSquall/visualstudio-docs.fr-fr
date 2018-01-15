---
title: Promise.race, fonction (Promise) | Documents Microsoft
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d35c448ad143facdcd783df0551505e440521b98
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2018
---
# <a name="promiserace-function-promise"></a>Promise.race, fonction (Promise)
Crée une promesse à résoudre ou rejeter avec la même valeur de résultat que la première promesse à résoudre ou rejeter parmi les arguments transmis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iterable`  
 Obligatoire. Une ou plusieurs promesses.  
  
## <a name="remarks"></a>Notes  
 Si l'une des promesses dans `iterable` est déjà dans un état résolu ou rejeté, `Promise.race` retourne une promesse résolue ou rejetée de la même façon avec la valeur de résultat égale à la valeur utilisée pour résoudre (ou rejeter) cette promesse. Si plusieurs promesses dans `iterable` sont déjà résolues ou rejetées, `Promise.race` retourne une promesse résolue de la même façon que la première promesse itérée. Si aucune promesse dans iterable n'est résolue ni rejetée, la promesse retournée par `Promise.race` n'est pas non plus résolue ni rejetée.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p3 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)
