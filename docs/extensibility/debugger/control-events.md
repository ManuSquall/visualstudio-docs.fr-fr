---
title: Événements de contrôle | Microsoft Docs
description: En savoir plus sur l’envoi d’événements pendant l’exécution contrôlée de votre programme à l’aide de l’interface IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb7249ece3ab38ff6f378f3c48ce36a995677604
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905694"
---
# <a name="control-events"></a>Événements de contrôle
Vous devez envoyer des événements pendant l’exécution contrôlée de votre programme. Tous les événements sont envoyés à l’aide de l’interface [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) et ont des attributs qui nécessitent que vous implémentiez la méthode [IDebugEvent2 :: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Autres méthodes
 Certains événements requièrent l’implémentation de méthodes supplémentaires, comme suit :

- L’envoi de l’interface [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) lorsque le moteur de débogage (de) est initialisé exige que vous implémentiez la méthode [IDebugEngineCreateEvent2 :: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Le contrôle d’exécution requiert l’implémentation d’événements de contrôle comme les interfaces [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) et[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** est requis uniquement pour les arrêts asynchrones.

- L’exécution pas à pas des fonctions requiert l’implémentation de l’interface [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) et de ses méthodes.

  Les événements dérivant des points d’arrêt requièrent l’implémentation des interfaces [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)et [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , ainsi que les méthodes [IDebugBreakpointBoundEvent2 :: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  L’évaluation d’expression asynchrone vous oblige à implémenter l’interface [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) et ses méthodes [IDebugExpressionEvaluationCompleteEvent2 :: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[et GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Les événements synchrones requièrent l’implémentation de la méthode [IDebugEngine2 :: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Pour que votre moteur écrive une sortie de type chaîne, vous devez implémenter la méthode [IDebugOutputStringEvent2 :: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>Voir aussi
- [Contrôle d’exécution et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
