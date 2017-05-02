---
title: "JsStartProfiling, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartProfiling"
helpviewer_keywords: 
  - "JsStartProfiling (fonction)"
ms.assetid: 638da395-42dd-4fc5-b581-819e647e887d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStartProfiling, fonction
Démarre le profilage dans le contexte actuel.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStartProfiling(  
   _In_ IActiveScriptProfilerCallback *callback,  
   _In_ PROFILER_EVENT_MASK eventMask,  
   _In_ unsigned long context  
);  
```  
  
#### Paramètres  
 `callback`  
 Rappel de profilage à utiliser.  
  
 `eventMask`  
 Événements de profilage avec lesquels effectuer le rappel.  
  
 `context`  
 Contexte à passer au rappel de profilage.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge dans les applications de bureau, mais ne l'est pas dans les applications du Windows Store.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)