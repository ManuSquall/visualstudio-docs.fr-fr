---
description: Obtient un contexte d’évaluation pour l’évaluation de l’expression dans le contexte actuel d’un frame de pile et d’un thread.
title: 'IDebugStackFrame2 :: GetExpressionContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4da07b438ca35417de025a0d9ec6c2dfa01f464d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053436"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Obtient un contexte d’évaluation pour l’évaluation de l’expression dans le contexte actuel d’un frame de pile et d’un thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Paramètres
`ppExprCxt`\
à Retourne un objet [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) qui représente un contexte pour l’évaluation de l’expression.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 En règle générale, un contexte d’évaluation de l’expression peut être considéré comme une étendue pour l’évaluation de l’expression. Appelez la méthode [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour analyser une expression, puis appelez les méthodes [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) résultantes pour évaluer l’expression analysée.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
