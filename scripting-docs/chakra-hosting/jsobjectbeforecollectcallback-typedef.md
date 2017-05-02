---
title: "JsObjectBeforeCollectCallback (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsObjectBeforeCollectCallback (typedef)
Rappel appelé avant la collecte d'un objet.  
  
## Syntaxe  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Paramètres  
 `ref`  
 Objet à collecter.  
  
 `callbackState`  
 État passé à `JsSetObjectBeforeCollectCallback`.  
  
## Notes  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)