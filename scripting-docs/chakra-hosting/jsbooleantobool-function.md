---
title: "JsBooleanToBool, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsBooleanToBool"
helpviewer_keywords: 
  - "JsBooleanToBool (fonction)"
ms.assetid: ab16ac71-fe47-475d-a7ee-46e4643dee60
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsBooleanToBool, fonction
Récupère la valeur `bool` d'une valeur booléenne.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsBooleanToBool(  
   _In_ JsValueRef value,  
   _Out_ bool *boolValue  
);  
```  
  
#### Paramètres  
 `value`  
 Valeur à convertir.  
  
 `boolValue`  
 Valeur convertie.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)