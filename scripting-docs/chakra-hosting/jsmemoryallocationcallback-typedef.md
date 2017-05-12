---
title: "JsMemoryAllocationCallback, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JsMemoryAllocationCallback, typedef
Routine de rappel implémentée par l'utilisateur pour les événements d'allocation mémoire.  
  
## Syntaxe  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### Paramètres  
 callbackState  
 L'état passé à JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Le type d'événement d'allocation de type.  
  
 allocationSize  
 La taille de l'allocation.  
  
## Valeur de propriété\/valeur de retour  
 Pour l'événement JsMemoryAllocate, le fait de retourner true autorise le runtime à continuer l'allocation.  Si false est retourné, cela signifie que la demande d'allocation est rejetée.  La valeur retournée est ignorée pour les autres événements d'allocation.  
  
## Notes  
 Utilisez JsSetRuntimeMemoryAllocationCallback pour inscrire ce rappel.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)