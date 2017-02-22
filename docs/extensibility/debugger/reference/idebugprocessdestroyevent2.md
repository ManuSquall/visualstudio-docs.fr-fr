---
title: "IDebugProcessDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProcessDestroyEvent2"
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcessDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée lorsqu'un processus est terminé, quitte atypiquement, ou est détachée de.  
  
## Syntaxe  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage ou le fournisseur de port implémentent cette interface pour signaler qu'un processus a été arrêté.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le De ou le fournisseur de port crée et envoie cet objet événement pour signaler l'arrêt d'un processus.  Le De envoie cet événement à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle est associée au programme en cours de débogage.  Le fournisseur de port envoie cet événement à l'aide de l'interface d' [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)