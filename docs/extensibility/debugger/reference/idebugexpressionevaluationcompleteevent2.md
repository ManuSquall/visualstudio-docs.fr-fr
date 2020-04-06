---
title: IDebugExpressionEvaluationCompleteEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35e57e361b59e76e187617b5e528b219e8e47897
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729561"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Cette interface est envoyée par le moteur de débogé (DE) au gestionnaire de débopathie de session (SDM) lorsque l’évaluation d’expression asynchrone est terminée.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE met en œuvre cette interface pour signaler l’achèvement d’une évaluation d’expression commencée par un appel à [AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler l’achèvement d’une évaluation d’expression. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme étant débogé.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugExpressionEvaluationCompleteEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtient l’expression originale.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtient le résultat de l’évaluation de l’expression.|

## <a name="remarks"></a>Notes
 Le DE doit envoyer cet événement, que l’évaluation ait été réussie ou non.

 Si l’évaluation n’a `DEBUG_PROPINFO_ATTRIB` pas été couronnée de succès, l’objet et les `DEBUG_PROPINFO_VALUE` drapeaux ne seront pas placés dans la structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui est retournée par [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (l’objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) est créé par le DE et retourné en cas `IDebugExpressionEvaluationCompleteEvent2` de échec de l’évaluation).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
