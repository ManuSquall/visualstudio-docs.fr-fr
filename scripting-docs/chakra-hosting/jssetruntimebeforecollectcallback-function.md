---
title: "JsSetRuntimeBeforeCollectCallback, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeBeforeCollectCallback"
helpviewer_keywords: 
  - "JsSetRuntimeBeforeCollectCallback (fonction)"
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeBeforeCollectCallback, fonction
Définit une fonction de rappel appelée par le runtime avant l'opération de garbage collection.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### Paramètres  
 `runtime`  
 Runtime pour lequel enregistrer le rappel d'allocation.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
 `beforeCollectCallback`  
 Fonction de rappel définie.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Le rappel est appelé sur le thread d'exécution du runtime actuel, par conséquent, l'exécution est bloquée jusqu'à ce que le rappel soit terminé.  
  
 Le rappel peut être utilisé par les hôtes pour préparer l'opération de garbage collection.  Par exemple, en libérant les références inutiles sur des objets Chakra.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)