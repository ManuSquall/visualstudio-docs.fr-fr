---
title: 'IDebugExpression2 :: EvaluateAsync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8af09c2db00b1f24631418c5332811cf4cb9202c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916265"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Cette méthode évalue l’expression de manière asynchrone.

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
dans Combinaison d’indicateurs de l’énumération [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui contrôlent l’évaluation de l’expression.

`pExprCallback`\
dans Ce paramètre est toujours une valeur null.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Voici un exemple de code d’erreur :

|Erreur|Description|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Une autre expression est actuellement en cours d’évaluation, et l’évaluation d’expression simultanée n’est pas prise en charge.|

## <a name="remarks"></a>Notes
Cette méthode doit être renvoyée immédiatement après le début de l’évaluation de l’expression. Lorsque l’expression est évaluée avec succès, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) doit être envoyé au rappel d’événement [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fourni via [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CExpression` objet simple qui implémente l’interface [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .

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
