---
title: "Fonction Debug.msTraceAsyncCallbackStarting | Microsoft Docs"
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Fonction Debug.msTraceAsyncCallbackStarting
Associe la pile de rappel à une opération asynchrone précédemment spécifiée.  
  
## Syntaxe  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### Paramètres  
 `asyncOperationId`  
 Requis.  ID associé à l'opération asynchrone.  
  
## Notes  
 Appelez cette fonction dans la fonction de rappel pour l'opération asynchrone après l'appel à `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Certains outils de débogage n'affichent pas les informations envoyées au débogueur.  
  
 `asyncOperationId` doit correspondre au nom d'opération précédemment retourné par `Debug.msTraceAsyncOperationStarting`.  
  
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