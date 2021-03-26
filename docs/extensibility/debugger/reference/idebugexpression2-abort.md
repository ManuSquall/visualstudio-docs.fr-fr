---
description: Cette méthode annule l’évaluation d’expression asynchrone telle qu’elle est démarrée par un appel à la méthode EvaluateAsync).
title: 'IDebugExpression2 :: Abort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6c355d2c4ee3cf63551f54b050b0ea42f4fdddc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092447"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Cette méthode annule l’évaluation d’expression asynchrone telle qu’elle est démarrée par un appel à la méthode [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lorsque l’évaluation d’une expression asynchrone est annulée, n’envoyez pas d’événement [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) au rappel d’événement passé aux méthodes [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
