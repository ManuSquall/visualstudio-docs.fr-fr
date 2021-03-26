---
title: IDebugExpressionContext2 | Microsoft Docs
description: Cette interface représente un contexte pour l’évaluation de l’expression
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6d8745207f1ab075aedd43815e7a97a4f0721bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092291"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Cette interface représente un contexte pour l’évaluation de l’expression.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) implémente cette interface pour représenter un contexte dans lequel une expression peut être évaluée.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne l’interface This. Cette interface est accessible uniquement lorsque le programme en cours de débogage a été suspendu et qu’un frame de pile est disponible.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExpressionContext2` .

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Récupère le nom du contexte d’évaluation.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analyse une expression basée sur du texte à des fins d’évaluation.|

## <a name="remarks"></a>Notes
 Un contexte d’évaluation peut être considéré comme une étendue pour effectuer une évaluation d’expression.

 Lorsqu’un programme s’est arrêté, le gestionnaire de débogage de session (SDM) obtient un frame de pile de l’un des appels à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour accéder à l' `IDebugExpressionContext2` interface. Ceci est suivi d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer une interface [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , qui représente l’expression analysée prête à être évaluée.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
