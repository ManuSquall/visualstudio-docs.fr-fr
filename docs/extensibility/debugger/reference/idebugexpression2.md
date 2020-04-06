---
title: IDebugExpression2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729688"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Cette interface représente une expression analysée prête à être contraignante et évaluante.

## <a name="syntax"></a>Syntaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter une expression analysée prête à être évaluée.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) renvoie cette interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne l’interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Ces interfaces ne sont accessibles que lorsque le programme en cours de déboisation a été interrompu et qu’un cadre de pile est disponible.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugExpression2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue cette expression asynchronement.|
|[Annuler](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation asynchrone d’expression.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue cette expression de façon synchrone.|

## <a name="remarks"></a>Notes
 Lorsqu’un programme s’est arrêté, le gestionnaire de déboptillement de session (SDM) obtient un cadre de pile de la DE avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir l’interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Il est suivi d’un appel à `IDebugExpression2` [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer l’interface, qui représente l’expression analysée prête à être évaluée.

 Le SDM appelle [Soit AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer réellement l’expression et produire une valeur.

 Dans une `IDebugExpressionContext2::ParseText`mise en œuvre `CoCreateInstance` de , le DE utilise la fonction de COM pour instantanéiser un évaluateur d’expression et obtenir une interface [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (voir l’exemple dans l’interface). `IDebugExpressionEvaluator` Le DE appelle ensuite [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir une interface [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Cette interface est utilisée `IDebugExpression2::EvaluateSync` dans `IDebugExpression2::EvaluateAsync` la mise en œuvre et pour effectuer l’évaluation.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
