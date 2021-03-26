---
description: Cette interface est envoyée par le moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsque l’évaluation de l’expression asynchrone est terminée.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092200"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Cette interface est envoyée par le moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsque l’évaluation de l’expression asynchrone est terminée.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler la fin de l’évaluation d’une expression lancée par un appel à [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler la fin de l’évaluation d’une expression. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpressionEvaluationCompleteEvent2` .

|Méthode|Description|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtient l’expression d’origine.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtient le résultat de l’évaluation de l’expression.|

## <a name="remarks"></a>Notes
 Le DE doit envoyer cet événement, que l’évaluation soit réussie ou non.

 Si l’évaluation n’a pas réussi, `DEBUG_PROPINFO_VALUE` les `DEBUG_PROPINFO_ATTRIB` indicateurs et ne sont pas définis dans la structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) retournée par [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (l’objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) est créé par le de et retourné dans l' `IDebugExpressionEvaluationCompleteEvent2` événement si l’évaluation a échoué).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
