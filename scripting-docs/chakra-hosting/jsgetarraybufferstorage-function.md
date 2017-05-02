---
title: "JsGetArrayBufferStorage (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetArrayBufferStorage (fonction)
Obtient le stockage sous\-jacent de mémoire utilisé par un `ArrayBuffer`.  
  
## Syntaxe  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### Paramètres  
 `arrayBuffer`  
 Instance de ArrayBuffer.  
  
 `buffer`  
 Mémoire tampon du ArrayBuffer.  La durée de vie de la mémoire tampon retournée est identique à la durée de vie du `ArrayBuffer`.  Le pointeur de la mémoire tampon ne compte pas comme une référence au `ArrayBuffer` pour le garbage collection.  
  
 `bufferLength`  
 Nombre d'octets dans la mémoire tampon.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)