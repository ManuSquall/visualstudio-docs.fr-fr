---
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56c0547d348c4fb3de387ac0ffce465b7bf5e90
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311785"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface représente une expression analysée prête à être évaluée.

## <a name="syntax"></a>Syntaxe

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter une expression analysée est prête pour l’évaluation.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) retourne cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente la méthode de `IDebugParsedExpression`.

|Méthode|Description|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Évalue l’expression analysée.|

## <a name="remarks"></a>Notes
 Lorsque l’appelant est prêt à évaluer l’expression, il appelle [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour retourner un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui contient le résultat de l’évaluation. Cette approche en deux parties pour évaluation, l’analyse puis évaluez, permet à l’expression analysée être évaluées plusieurs fois, en contournant le processus fastidieux de l’analyse de l’expression.

## <a name="requirements"></a>Configuration requise
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)