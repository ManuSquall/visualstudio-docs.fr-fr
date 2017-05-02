---
title: "JsMemoryEventType, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType (énumération)"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType, &#233;num&#233;ration
Type d'événement de rappel d'allocation.  
  
## Syntaxe  
  
```  
enum JsMemoryEventType;  
```  
  
## Membres  
  
### Valeurs  
  
|Nom|Description|  
|---------|-----------------|  
|`JsMemoryAllocate`|Indique une demande d'allocation de mémoire.|  
|`JsMemoryFailure`|Indique l'échec d'un événement d'allocation.|  
|`JsMemoryFree`|Indique un événement de libération de mémoire.|  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)