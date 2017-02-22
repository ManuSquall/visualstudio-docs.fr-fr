---
title: "IDebugBreakpointBoundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointBoundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2"
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointBoundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface indique au gestionnaire de débogage de session \(SDM\) qu'un point d'arrêt en attente a été correctement lié à un programme chargé.  
  
## Syntaxe  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'un point d'arrêt en attente est correctement lié au programme en cours de débogage.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointBoundEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|obtient le point d'arrêt en attente qui est lié.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|crée un énumérateur des points d'arrêt qui ont été liés sur cet événement.|  
  
## Notes  
 Chaque fois qu'un point d'arrêt est lié, un événement est envoyé au SDM.  Si le point d'arrêt ne peut pas être liée, [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) est envoyé ; sinon, `IDebugBreakpointBoundEvent2` est envoyé.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)