---
title: "JsStartDebugging, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging (fonction)"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsStartDebugging, fonction
Démarre le débogage dans le contexte actuel.  
  
## Syntaxe  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### Paramètres  
 `debugApplication`  
 Application de débogage à utiliser pour le débogage.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 L'hôte doit s'assurer que `CoInitializeEx` est appelé avec `COINIT_MULTITHREADED` ou `COINIT_APARTMENTTHREADED` au moins une fois avant d'utiliser cette API  
  
 Le paramètre `debugApplication` n'est pas pris en charge dans le mode Edge.  Pour plus d'informations sur l'utilisation de cette API dans le mode Edge, consultez [Ciblage du moteur Edge ou des moteurs hérités](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)