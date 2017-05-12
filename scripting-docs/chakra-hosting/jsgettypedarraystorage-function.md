---
title: "JsGetTypedArrayStorage (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetTypedArrayStorage (fonction)
Obtient le stockage sous\-jacent de mémoire utilisé par un tableau typé.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### Paramètres  
 `typedArray`  
 Instance de tableau typé.  
  
 `buffer`  
 Mémoire tampon du tableau.  La durée de vie de la mémoire tampon retournée est identique à la durée de vie du tableau.  Le pointeur de la mémoire tampon ne compte pas comme une référence au tableau pour le garbage collection.  
  
 `bufferLength`  
 Nombre d'octets dans la mémoire tampon.  
  
 `arrayType`  
 Type de tableau.  
  
 `elementSize`  
 Taille d'un élément du tableau.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)