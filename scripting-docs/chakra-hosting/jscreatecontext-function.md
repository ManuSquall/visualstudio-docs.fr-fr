---
title: "JsCreateContext, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext (fonction)"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext, fonction
Crée un contexte de script pour exécuter des scripts.  
  
## Syntaxe  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### Paramètres  
 `runtime`  
 Runtime dans lequel le contexte de script est créé.  
  
 `debugApplication`  
 Application de débogage à utiliser pour le débogage.  Ce paramètre peut être null, auquel cas le débogage n'est pas activé pour le contexte.  
  
 `newContext`  
 Contexte de script créé.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Chaque contexte de script possède son propre objet global, qui est isolé des autres contextes de script.  
  
 Le paramètre `debugApplication` n'est pas pris en charge dans le mode Edge.  Pour plus d'informations sur l'utilisation de cette API dans le mode Edge, consultez [Ciblage du moteur Edge ou des moteurs hérités](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)