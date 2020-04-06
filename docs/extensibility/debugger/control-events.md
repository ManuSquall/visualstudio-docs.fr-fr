---
title: Événements de contrôle (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739087"
---
# <a name="control-events"></a>Événements de contrôle
Vous devez envoyer des événements lors de l’exécution contrôlée de votre programme. Tous les événements sont envoyés à l’aide de [l’interface IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) et ont des attributs qui vous obligent à implémenter la méthode [IDebugEvent2:GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Méthodes supplémentaires
 Certains événements nécessitent la mise en œuvre de méthodes supplémentaires, comme suit :

- L’envoi de [l’interface IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) lorsque le moteur de débogé (DE) est initialisé vous oblige à implémenter la méthode [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) méthode.

- Le contrôle d’exécution nécessite la mise en œuvre d’événements de contrôle tels que les interfaces [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) et[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** n’est nécessaire que pour les pauses asynchrones.

- Entrer dans les fonctions nécessite la mise en œuvre de [l’interface IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) et de ses méthodes.

  Les événements dérivés des points d’arrêt nécessitent la mise en œuvre des interfaces [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), et [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ainsi que les méthodes [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) méthodes.

  L’évaluation d’expression asynchrone vous oblige à implémenter [l’interface IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) et ses méthodes [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[et GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) méthodes.

  Les événements synchrones nécessitent la mise en œuvre de la méthode [IDebugEngine2::ContinueDeSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Pour que votre moteur écrive la sortie de style chaîne, vous devez implémenter la méthode [IDebugOutputStringEvent2::GetString.](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)

## <a name="see-also"></a>Voir aussi
- [Contrôle des exécutions et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
