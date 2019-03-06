---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b5b58a5be5321c2f867daa5b46a7671dbae5d8e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700573"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour le Gestionnaire de session de débogage (SDM) lors de l’évaluation de l’expression asynchrone est terminée.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface jusqu'à la fin du rapport d’une évaluation d’expression démarrée par un appel à [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler l’achèvement d’une évaluation d’expression. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpressionEvaluationCompleteEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtient l’expression d’origine.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtient le résultat de l’évaluation de l’expression.|

## <a name="remarks"></a>Notes
 Le DE doit envoyer cet événement, si l’évaluation a réussi ou non.

 Si la version d’évaluation n’a pas réussie, le `DEBUG_PROPINFO_VALUE` et `DEBUG_PROPINFO_ATTRIB` indicateurs ne seront pas définis le [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure qui est retournée par [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet est créé par l’Allemagne et retournée dans le `IDebugExpressionEvaluationCompleteEvent2` événement en cas d’échec de la version d’évaluation).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)