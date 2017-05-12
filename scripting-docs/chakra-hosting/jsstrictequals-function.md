---
title: "JsStrictEquals, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStrictEquals"
helpviewer_keywords: 
  - "JsStrictEquals (fonction)"
ms.assetid: b35bc655-7ff8-496a-b678-8950bb976047
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStrictEquals, fonction
Comparez deux valeurs JavaScript pour vérifier leur égalité stricte.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStrictEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### Paramètres  
 `object1`  
 Premier objet à comparer.  
  
 `object2`  
 Deuxième objet à comparer.  
  
 `result`  
 Indique si les valeurs sont strictement égales.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Cette fonction est équivalente à l'opérateur `===` en Javascript.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)