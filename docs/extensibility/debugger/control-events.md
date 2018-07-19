---
title: Événements de contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40e07e480a89629da919af9d6542b2879c49718f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101659"
---
# <a name="control-events"></a>Événements de contrôle
Vous devez envoyer des événements pendant l’exécution contrôlée de votre programme. Tous les événements sont envoyés à l’aide de la [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) interfaces et avoir des attributs qui requièrent une vous permet d’implémenter le [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) (méthode).  
  
## <a name="additional-methods"></a>Méthodes supplémentaires  
 Certains événements nécessitent l’implémentation des méthodes supplémentaires, comme suit :  
  
-   Envoi de la [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface lorsque le moteur de débogage (DE) est initialisé, vous devez implémenter la [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) (méthode).  
  
-   Contrôle de l’exécution nécessite l’implémentation des événements de contrôle tels que les [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) et[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaces. **IDebugBreakEvent2** est requis uniquement pour les sauts asynchrones.  
  
-   Pas à pas détaillé dans les fonctions nécessite l’implémentation de la [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface et ses méthodes.  
  
 Dérivation à partir de points d’arrêt des événements requièrent l’implémentation de la [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), et [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaces, ainsi que le [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) méthodes.  
  
 Évaluation de l’expression asynchrone, vous devez implémenter la [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface et son [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [et GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) méthodes.  
  
 Événements synchrones nécessitent la mise en œuvre le [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) (méthode).  
  
 Pour votre moteur écrire la sortie de chaîne-style, vous devez implémenter la [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)