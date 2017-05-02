---
title: "JsSetException, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException (fonction)"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException, fonction
Définit le runtime du contexte actuel dans un état d'exception.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### Paramètres  
 `exception`  
 Exception JavaScript à définir pour le runtime du contexte actuel.  
  
## Valeur de retour  
 `JsNoError` si le moteur a été défini dans un état d'exception, sinon, un code d'erreur.  
  
## Notes  
 Si le runtime du contexte actuel est déjà dans un état d'exception, cette API retourne `JsErrorInExceptionState`.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)