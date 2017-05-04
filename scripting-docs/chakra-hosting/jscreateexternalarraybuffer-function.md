---
title: "JsCreateExternalArrayBuffer (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsCreateExternalArrayBuffer (fonction)
Crée un objet `ArrayBuffer` Javascript pour accéder à la mémoire externe.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### Paramètres  
 `data`  
 Pointeur vers la mémoire externe.  
  
 `byteLength`  
 Nombre d’octets dans la mémoire externe.  
  
 `finalizeCallback`  
 Rappel au moment où l'objet est finalisé. Ce paramètre peut être null.  
  
 `callbackState`  
 État fourni par l’utilisateur qui sera repassé à finalizeCallback.  
  
 `result`  
 Nouvel objet `ArrayBuffer`.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)