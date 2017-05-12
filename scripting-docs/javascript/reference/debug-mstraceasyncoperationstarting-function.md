---
title: "Fonction Debug.msTraceAsyncOperationStarting | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Fonction Debug.msTraceAsyncOperationStarting
Initialise une trace pour une opération asynchrone.  
  
## Syntaxe  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### Paramètres  
 `operationName`  
 Requis.  Chaîne qui identifie l'opération asynchrone.  Si `operationName` a une valeur null ou n'est pas défini, une chaîne vide est utilisée pour le nom de l'opération.  
  
## Valeur de retour  
 Entier représentant l'ID d'opération.  
  
## Notes  
 Appelez cette méthode avant le début de l'opération asynchrone.  
  
> [!NOTE]
>  Certains outils de débogage n'affichent pas les informations envoyées au débogueur.  
  
## Exemple  
 Le code suivant fournit un exemple d'instrumentation d'un appel asynchrone pour une application [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
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