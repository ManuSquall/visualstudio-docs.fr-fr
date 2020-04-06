---
title: IDebugExpression2::EvaluateAsync Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729755"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Cette méthode évalue l’expression asynchrone.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Paramètres
`dwFlags`\
[dans] Une combinaison de drapeaux du recensement [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui contrôlent l’évaluation de l’expression.

`pExprCallback`\
[dans] Ce paramètre est toujours une valeur nulle.

## <a name="return-value"></a>Valeur de retour
En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur. Un code d’erreur typique est :

|Error|Description|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Une autre expression est actuellement en cours d’évaluation, et l’évaluation simultanée de l’expression n’est pas étayée.|

## <a name="remarks"></a>Notes
Cette méthode devrait revenir immédiatement après avoir commencé l’évaluation de l’expression. Lorsque l’expression est évaluée avec succès, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) doit être envoyé à [l’IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) rappel événement tel qu’il est fourni par [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet simple `CExpression` qui implémente [l’interface IDebugExpression2.](../../../extensibility/debugger/reference/idebugexpression2.md)

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
