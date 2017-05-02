---
title: "JsStopProfiling, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStopProfiling"
helpviewer_keywords: 
  - "JsStopProfiling (fonction)"
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStopProfiling, fonction
Arrête le profilage dans le contexte actuel.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### Paramètres  
 `reason`  
 Raison pour laquelle le profilage cesse de transmettre au rappel de profileur.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Ne retourne pas d'erreur si le profilage n'a pas démarré.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge dans les applications de bureau, mais ne l'est pas dans les applications du Windows Store.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)