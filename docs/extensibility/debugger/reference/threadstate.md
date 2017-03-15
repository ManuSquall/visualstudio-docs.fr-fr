---
title: "&#201;TATS DU THREAD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADSTATE"
helpviewer_keywords: 
  - "Énumération THREADSTATE"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;TATS DU THREAD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie l'état du thread.  
  
## Syntaxe  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## Membres  
 THREADSTATE\_RUNNING  
 Indique que le thread s'exécute.  
  
 THREADSTATE\_STOPPED  
 Indique que le thread est arrêté en raison d'un point d'arrêt.  
  
 THREADSTATE\_FRESH  
 indique que le thread a été créé, mais n'exécute pas encore code.  
  
 THREADSTATE\_DEAD  
 Indique que le thread est inactif.  
  
 THREADSTATE\_FROZEN  
 Indique que le thread est gelé \(aucune exécution ne peut être exécutée\).  
  
## Notes  
 utilisé pour le champ d' `dwThreadState` de la structure de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)