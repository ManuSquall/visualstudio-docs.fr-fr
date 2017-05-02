---
title: "JsStringToPointer, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer (fonction)"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer, fonction
Récupère le pointeur de chaîne d'une valeur de chaîne.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### Paramètres  
 `value`  
 Valeur de chaîne à convertir en pointeur de chaîne.  
  
 `stringValue`  
 Pointeur de chaîne.  
  
 `stringLength`  
 Longueur de la chaîne.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Cette fonction récupère le pointeur de chaîne d'une valeur de chaîne.  Elle échoue avec `JsErrorInvalidArgument` si le type de la valeur n'est pas une chaîne.  La durée de vie de la chaîne retournée est identique à celle de la valeur dont elle provient, toutefois, le pointeur de chaîne n'est pas considéré comme une référence à la valeur \(et donc ne l'empêchera pas d'être collectée\).  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)