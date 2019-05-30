---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ad9c3d6bb1b0a5baccbcf5bf47eb02a8bb5efa5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325853"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Cette interface représente un contexte pour l’évaluation d’expression

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter un contexte dans lequel une expression peut être évaluée.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne cette interface. Cette interface est accessible uniquement lorsque le programme en cours de débogage a été suspendu et un frame de pile est disponible.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpressionContext2`.

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Récupère le nom du contexte d’évaluation.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analyse une expression basée sur le texte pour l’évaluation.|

## <a name="remarks"></a>Notes
 Un contexte d’évaluation peut être considéré comme une étendue pour effectuer l’évaluation de l’expression.

 Lorsqu’un programme s’est arrêté, le Gestionnaire de session de débogage (SDM) Obtient un frame de pile à partir de l’Allemagne avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le `IDebugExpressionContext2` interface. Elle est suivie d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interface, qui représente l’expression analysée prête à être évaluée.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)