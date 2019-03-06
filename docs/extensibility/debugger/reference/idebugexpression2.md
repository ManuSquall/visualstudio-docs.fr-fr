---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8027f34b48b4a160c19f14f0d9cbfb8194a506f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688471"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Cette interface représente un prêt de l’expression analysée de liaison et d’évaluation.

## <a name="syntax"></a>Syntaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter une expression analysée prête à être évaluée.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retourne cette interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne le [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Ces interfaces sont accessibles uniquement lorsque le programme en cours de débogage a été suspendu et un frame de pile est disponible.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpression2`.

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue cette expression de façon asynchrone.|
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue cette expression de façon synchrone.|

## <a name="remarks"></a>Notes
 Lorsqu’un programme s’est arrêté, le Gestionnaire de session de débogage (SDM) Obtient un frame de pile à partir de l’Allemagne avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Elle est suivie d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer le `IDebugExpression2` interface, qui représente l’expression analysée prête à être évaluée.

 Appelle le SDM [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression et produire une valeur.

 Dans une implémentation de `IDebugExpressionContext2::ParseText`, l’Allemagne utilise de COM `CoCreateInstance` fonction pour instancier un évaluateur d’expression et obtenir un [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface (consultez l’exemple dans le `IDebugExpressionEvaluator` interface). Le D’appelle ensuite [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Cette interface est utilisée dans l’implémentation de `IDebugExpression2::EvaluateSync` et `IDebugExpression2::EvaluateAsync` pour effectuer l’évaluation.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)