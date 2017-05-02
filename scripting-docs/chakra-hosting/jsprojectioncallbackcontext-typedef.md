---
title: "JsProjectionCallbackContext (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext (typedef)
Contexte passé dans le rappel de l'application, JsProjectionEnqueueCallback, de JsRT et ensuite repassé à JsRT dans le rappel fourni, `JsProjectionCallback`, par l'application sur le thread approprié.  
  
## Syntaxe  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## Notes  
 Nécessite l'appel de `JsSetProjectionEnqueueCallback` pour recevoir des rappels.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)