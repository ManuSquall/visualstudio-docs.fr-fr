---
title: "Fonction JsGetTypedArrayInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Fonction JsGetTypedArrayInfo
Obtient les propriétés fréquemment utilisées d’un tableau typé.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### Paramètres  
 `typedArray`  
 Instance de tableau typé.  
  
 `arrayType`  
 Type de tableau.  
  
 `arrayBuffer`  
 Stockage de secours `ArrayBuffer` du tableau.  
  
 `byteOffset`  
 Décalage en octets à partir du début d’arrayBuffer référencé par le tableau.  
  
 `byteLength`  
 Nombre d'octets dans le tableau.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)