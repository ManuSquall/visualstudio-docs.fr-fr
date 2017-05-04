---
title: "JsProjectionEnqueueCallback (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback (typedef)
Rappel d'application effectué par JsRT quand une API de projection est exécutée sur un thread différent de celui d'origine.  
  
## Syntaxe  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Paramètres  
 `jsCallback`  
 Rappel à effectuer sur le thread d'origine.  
  
 `jsContext`  
 Contexte des applications.  
  
 `callbackState`  
 Contexte JsRT qui doit être passé dans `jsCallback`.  
  
## Notes  
 Nécessite l'appel de JsSetProjectionEnqueueCallback pour recevoir des rappels.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)