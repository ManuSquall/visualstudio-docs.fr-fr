---
title: "JsIsRuntimeExecutionDisabled, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled (fonction)"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled, fonction
Retourne une valeur qui indique si l'exécution du script est désactivée dans le runtime.  
  
## Syntaxe  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### Paramètres  
 `runtime`  
 Spécifie le runtime pour lequel vérifier que l'exécution est désactivée.  
  
 `isDisabled`  
 `true` si l'exécution est désactivée ; sinon, `false`.  
  
## Valeur de retour  
 `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)