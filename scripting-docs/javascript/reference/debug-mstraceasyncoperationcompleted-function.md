---
title: "Fonction Debug.msTraceAsyncOperationCompleted | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Fonction Debug.msTraceAsyncOperationCompleted
Indique qu'une opération asynchrone a été effectuée.  
  
## Syntaxe  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### Paramètres  
 `asyncOperationId`  
 Requis.  ID associé à une opération asynchrone.  
  
 `status`  
 Facultatif.  État de l'opération asynchrone.  En l'absence de spécification, `Debug.MS_ASYNC_OP_STATUS_SUCCESS` est utilisé.  
  
## Notes  
 Appelez cette fonction lorsque l'opération asynchrone se termine.  
  
 `asyncOperationId` doit correspondre à l'ID d'opération précédemment retourné par `Debug.msTraceAsyncOperationStarting`.  
  
 Les valeurs possibles pour `status` sont les suivantes :  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Certains outils de débogage n'affichent pas les informations envoyées au débogueur.  
  
## Exemple  
 Le code suivant fournit un exemple de traçage d'un appel asynchrone pour une application [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]