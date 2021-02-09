---
title: IDebugExpressionContext2 ::P arseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc55cceb8db392d590ff414ac3df5b807d1e52e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901646"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analyse une expression sous forme de texte pour une évaluation ultérieure.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Paramètres
`pszCode`\
dans Expression à analyser.

`dwFlags`\
dans Combinaison d’indicateurs de l’énumération [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) qui contrôle l’analyse.

`nRadix`\
dans Base à utiliser pour l’analyse de toutes les informations numériques dans `pszCode` .

`ppExpr`\
à Retourne l’objet [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) qui représente l’expression analysée, qui est prête pour la liaison et l’évaluation.

`pbstrError`\
à Retourne le message d’erreur si l’expression contient une erreur.

`pichError`\
à Retourne l’index de caractère de l’erreur dans `pszCode` si l’expression contient une erreur.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
Lorsque cette méthode est appelée, un moteur DE débogage (DE) doit analyser l’expression et la valider pour l’exactitude. Les `pbstrError` `pichError` paramètres et peuvent être remplis si l’expression n’est pas valide.

Notez que l’expression n’est pas évaluée, analysée uniquement. Un appel ultérieur aux méthodes [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) évalue l’expression analysée.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CEnvBlock` objet simple qui expose l’interface [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Cet exemple considère que l’expression doit être analysée en tant que nom d’une variable d’environnement et récupère la valeur de cette variable.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
