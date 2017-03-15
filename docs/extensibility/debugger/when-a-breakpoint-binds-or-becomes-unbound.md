---
title: "Lorsqu&#39;un point d&#39;arr&#234;t est li&#233; ou devient ind&#233;pendant | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), point d'arrêt indépendant des événements"
  - "point d'arrêt lié des événements"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Lorsqu&#39;un point d&#39;arr&#234;t est li&#233; ou devient ind&#233;pendant
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsqu'un point d'arrêt ne peut pas être liée ensuite un appel est passé à la méthode d' [IDebugPendingBreakpoint2 : : CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , le temps de liaison et l'heure de création du point d'arrêt est différente.  
  
## méthodes appelées  
 le gestionnaire de débogage de session \(SDM\) appelle les méthodes suivantes :  
  
1.  [IDebugEngine2 : : CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  Le De retourne [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2.  [IDebugPendingBreakpoint2 : : Vérifiez](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3.  [IDebugPendingBreakpoint2 : : virtualisez](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4.  La méthode et retourne S\_OK d' [IDebugPendingBreakpoint2 : : Liaison](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .  Le De envoie [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5.  Méthodes d'[IDebugBreakpointBoundEvent2 : : GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et d' [IDebugBreakpointBoundEvent2 : : EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) pour vérifier et obtenir des points d'arrêt liés.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)