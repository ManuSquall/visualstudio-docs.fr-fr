---
title: "JsSetRuntimeMemoryLimit, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit (fonction)"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryLimit, fonction
Définit la limite de mémoire actuelle pour un runtime.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### Paramètres  
 `runtime`  
 Runtime dont la limite de mémoire doit être définie.  
  
 `memoryLimit`  
 Nouvelle limite de mémoire du runtime, en octets, ou \-1 pour aucune limite de mémoire.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Une limite de mémoire entraîne l'échec de toute opération qui dépasse la limite avec une erreur « mémoire insuffisante ».  La définition de la limite de mémoire d'un runtime avec la valeur \-1 signifie que le runtime n'a aucune limite de mémoire.  Par défaut, les nouveaux runtimes n'ont pas de limite de mémoire.  Si la nouvelle limite de mémoire dépasse l'utilisation actuelle, l'appel réussi et toutes les futures allocations dans ce runtime échouent tant que l'utilisation de la mémoire du runtime ne descend pas en dessous de la limite.  
  
 La limite de mémoire d'un runtime peut toujours être définie, que le runtime soit actif ou non sur un autre thread.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)