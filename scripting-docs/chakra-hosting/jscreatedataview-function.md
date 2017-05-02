---
title: "JsCreateDataView (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateDataView (fonction)
Crée un objet `DataView` Javascript.  
  
## Syntaxe  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Paramètres  
 `arrayBuffer`  
 Objet `ArrayBuffer` existant à utiliser comme stockage pour l'objet résultat `DataView`.  
  
 `byteOffset`  
 Décalage en octets du début de l'objet `arrayBuffer` pour l'objet résultat `DataView` à la référence.  
  
 `byteLength`  
 Nombre d'octets dans l'objet ArrayBuffer pour l'objet résultat DataView à référencer.  
  
 `result`  
 Nouvel objet DataView.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)