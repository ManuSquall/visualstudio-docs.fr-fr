---
title: Fonction Debug.msTraceAsyncOperationCompleted | Documents Microsoft
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
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636229"
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Fonction Debug.msTraceAsyncOperationCompleted
Indique qu'une opération asynchrone a été effectuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `asyncOperationId`  
 Obligatoire. ID associé à une opération asynchrone.  
  
 `status`  
 Facultatif. État de l'opération asynchrone. En l'absence de spécification, `Debug.MS_ASYNC_OP_STATUS_SUCCESS` est utilisé.  
  
## <a name="remarks"></a>Remarques  
 Appelez cette fonction lorsque l'opération asynchrone se termine.  
  
 `asyncOperationId` doit correspondre à l'ID d'opération précédemment retourné par `Debug.msTraceAsyncOperationStarting`.  
  
 Les valeurs possibles pour `status` sont les suivantes :  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Certains outils de débogage n'affichent pas les informations envoyées au débogueur.  
  
## <a name="example"></a>Exemple  
 Le code suivant fournit un exemple de traçage d'un appel asynchrone pour une application [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```JavaScript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]