---
title: "Fonction Debug.msTraceAsyncCallbackCompleted | Microsoft Docs"
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
ms.assetid: 6f9bf139-a6f0-4d91-b7bf-bcc0515de686
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Fonction Debug.msTraceAsyncCallbackCompleted
Indique que la pile de rappel associée à une opération asynchrone précédemment spécifiée est terminée.  
  
## Syntaxe  
  
```  
Debug.msTraceAsyncCallbackCompleted()  
```  
  
## Notes  
 Appelez cette fonction après l'appel à `Debug.msTraceAsyncCallbackStarting`.  
  
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