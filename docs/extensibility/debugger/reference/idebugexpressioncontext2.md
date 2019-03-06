---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 559115358910fe3445ab12000d1e113167c7da82
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717986"
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

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)