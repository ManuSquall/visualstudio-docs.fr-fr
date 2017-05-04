---
title: "JsProjectionCallback (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback (typedef)
Rappel JsRT qui doit être appelé avec le contexte transmis à `JsProjectionEnqueueCallback` sur le thread approprié.  
  
## Syntaxe  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Paramètres  
 `jsContext`  
 Nécessite l'appel de `JsSetProjectionEnqueueCallback` pour recevoir des rappels.  
  
## Notes  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)