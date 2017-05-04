---
title: "JsGetAndClearException, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException (fonction)"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetAndClearException, fonction
Retourne l'exception qui a provoqué l'état d'exception du runtime du contexte actuel et réinitialise l'état d'exception pour ce runtime.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### Paramètres  
 `exception`  
 Exception pour le runtime du contexte actuel.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Si le runtime du contexte actuel n'est pas dans un état d'exception, cette API retourne `JsErrorInvalidArgument`.  Si le runtime est désactivé, il retourne une exception indiquant que le script a été arrêté, mais il ne désactive pas l'exception \(elle est désactivée si le runtime est réactivé à l'aide de `JsEnableRuntimeExecution`\).  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)