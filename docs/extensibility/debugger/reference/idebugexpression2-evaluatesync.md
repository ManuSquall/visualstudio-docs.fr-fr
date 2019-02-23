---
title: IDebugExpression2::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 158e24a57838d7f7a1c7221fc243455b5a4bd2bc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678551"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Cette méthode évalue l’expression de façon synchrone.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

#### <a name="parameters"></a>Paramètres
`dwFlags`

 [in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui contrôlent l’évaluation de l’expression.

`dwTimeout`

 [in] Durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`pExprCallback`

 [in] Ce paramètre est toujours une valeur null.

`ppResult`

 [out] Retourne le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui contient le résultat de l’évaluation d’expression.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Certains codes d’erreur standard sont :

|Error|Description|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Une autre expression est en cours d’évaluation et évaluation de l’expression simultanées n’est pas pris en charge.|
|E_EVALUATE_TIMEOUT|Version d’évaluation a expiré.|

## <a name="remarks"></a>Notes
Pour l’évaluation synchrone, il n’est pas nécessaire envoyer un événement vers Visual Studio à l’achèvement de l’évaluation.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour une simple `CExpression` objet qui implémente le [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interface.

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
