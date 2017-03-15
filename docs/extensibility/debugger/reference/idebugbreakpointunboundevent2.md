---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface indique au gestionnaire de débogage de session \(SDM\) qu'un point d'arrêt lié a été annulé la liaison d'un programme chargé.  
  
## Syntaxe  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de \(DE\) débogage implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'un point d'arrêt lié a été annulé la liaison.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointUnboundEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Obtient le point d'arrêt qui a été indépendant.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|obtient la raison que le point d'arrêt a été annulé la liaison.|  
  
## Notes  
 Lorsqu'une DLL du moteur de débogage ou une classe décharge, tous les points d'arrêt qui ont été liés au code dans ce module doivent être annulés la liaison du programme débogué.  `IDebugBreakpointUnboundEvent2` est envoyé pour chaque point d'arrêt indépendant.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)