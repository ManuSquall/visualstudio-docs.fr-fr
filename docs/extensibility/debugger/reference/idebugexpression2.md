---
description: Cette interface représente une expression analysée prête pour la liaison et l’évaluation.
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fe6a6955f5d8d4ae42d51e3623b0c4f966dc416
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152661"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Cette interface représente une expression analysée prête pour la liaison et l’évaluation.

## <a name="syntax"></a>Syntaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) implémente cette interface pour représenter une expression analysée prête à être évaluée.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retourne cette interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne l’interface [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Ces interfaces sont accessibles uniquement lorsque le programme en cours de débogage a été suspendu et qu’un frame de pile est disponible.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpression2` .

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue cette expression de manière asynchrone.|
|[Abandon](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue cette expression de façon synchrone.|

## <a name="remarks"></a>Notes
 Lorsqu’un programme s’est arrêté, le gestionnaire de débogage de session (SDM) obtient un frame de pile de l’un des appels à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour accéder à l’interface [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Ceci est suivi d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer l' `IDebugExpression2` interface, qui représente l’expression analysée prête à être évaluée.

 Le SDM appelle soit [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , soit [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer réellement l’expression et produire une valeur.

 Dans une implémentation de `IDebugExpressionContext2::ParseText` , le de utilise la fonction de com `CoCreateInstance` pour instancier un évaluateur d’expression et obtenir une interface [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (Voir l’exemple dans l' `IDebugExpressionEvaluator` interface). Le appelle ensuite [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir une interface [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Cette interface est utilisée dans l’implémentation de `IDebugExpression2::EvaluateSync` et `IDebugExpression2::EvaluateAsync` pour effectuer l’évaluation.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
