---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface indique au gestionnaire de débogage de session \(SDM\) qu'un point d'arrêt en attente ne peut pas être liée à un programme chargé, à cause d'un avertissement ou une erreur.  
  
## Syntaxe  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'un point d'arrêt en attente ne peut pas être lié au programme en cours de débogage.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointErrorEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|obtient l'interface d' [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) qui décrit l'avertissement ou l'erreur.|  
  
## Notes  
 Chaque fois qu'un point d'arrêt est lié, un événement est envoyé au SDM.  Si le point d'arrêt ne peut pas être liée, `IDebugBreakpointErrorEvent2` est envoyé ; sinon, [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) est envoyé.  
  
 Par exemple, lorsque la condition associée au point d'arrêt en attente n'analyse pas ou ne correspond pas, il envoie un avertissement indiquant que le point d'arrêt en attente ne peut pas être liée à ce stade.  Cela peut se produire si le code de le point d'arrêt n'a pas encore chargé.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)