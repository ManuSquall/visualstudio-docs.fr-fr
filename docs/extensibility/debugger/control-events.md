---
title: "&#201;v&#233;nements de contr&#244;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], événements"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# &#201;v&#233;nements de contr&#244;le
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous devez envoyer des événements pendant l'exécution contrôlée de votre programme.  Tous les événements sont envoyés à l'aide de l'interface d' [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) et ont des attributs qui requièrent que vous pour implémenter la méthode d' [IDebugEvent2 : : GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .  
  
## méthodes supplémentaires  
 Certains événements requièrent l'implémentation des méthodes supplémentaires, comme suit :  
  
-   Envoyer l'interface d' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) lorsque le moteur de \(DE\) débogage est initialisé vous obligent à implémenter la méthode d' [IDebugEngineCreateEvent2 : : GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .  
  
-   Le contrôle d'exécution requiert l'implémentation des événements de ce type de contrôle que les interfaces d' [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) et d'[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) .  **IDebugBreakEvent2** est obligatoire uniquement pour les sauts asynchrones.  
  
-   La progression dans les fonctions requiert l'implémentation de l'interface d' [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) et de ses méthodes.  
  
 Les événements dérivant des points d'arrêt requièrent l'implémentation des interfaces d' [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), d' [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), et d' [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , ainsi que des méthodes d' [IDebugBreakpointBoundEvent2 : : GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et d' [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .  
  
 L'évaluation d'une expression asynchrone vous obligent à appliquer l'interface d' [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) et ses méthodes d' [IDebugExpressionEvaluationCompleteEvent2 : : GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[et GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .  
  
 Les événements synchrones requièrent l'implémentation de la méthode d' [IDebugEngine2 : : ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) .  
  
 Pour que votre moteur a écrit la sortie de style de la chaîne, vous devez implémenter la méthode d' [IDebugOutputStringEvent2 : : GetString](../Topic/IDebugOutputStringEvent2::GetString.md) .  
  
## Voir aussi  
 [Contrôle de l'exécution et l'évaluation de l'état](../../extensibility/debugger/execution-control-and-state-evaluation.md)