---
title: Exemple de mise en œuvre de l’évaluation de l’expression (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713097"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemple de mise en œuvre de l’évaluation de l’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon de l’évaluateur de l’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Pour une expression de fenêtre **de montre,** Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour produire un objet [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`instantanét un évaluateur d’expression (EE) et appelle [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un objet [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Les `IDebugExpressionEvaluator::Parse` tâches suivantes exécutent :

1. [C seulement] Parses l’expression pour rechercher des erreurs.

2. Instantiates une classe `CParsedExpression` (appelée dans cet `IDebugParsedExpression` exemple) qui exécute l’interface et stocke dans la classe l’expression à analyser.

3. Retourne `IDebugParsedExpression` l’interface `CParsedExpression` de l’objet.

> [!NOTE]
> Dans les exemples qui suivent et dans l’échantillon MyCEE, l’évaluateur de l’expression ne sépare pas l’analyse de l’évaluation.

## <a name="managed-code"></a>Code managé
 Le code suivant montre `IDebugExpressionEvaluator::Parse` une implémentation de code géré. Cette version de la méthode reporte l’analyse à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que le code d’analyse évalue également en même temps (voir [Évaluer une expression de montre](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Code non-gestion
Le code suivant est `IDebugExpressionEvaluator::Parse` une implémentation de code non menté. Cette méthode appelle une `Parse`fonction d’aide, , pour analyser l’expression et vérifier les erreurs, mais cette méthode ignore la valeur résultante. L’évaluation formelle est reportée à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) où l’expression est analysée pendant qu’elle est évaluée (voir [Évaluer une expression de montre](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [Évaluer l’expression d’une fenêtre de montre](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Évaluer l’expression d’une montre](../../extensibility/debugger/evaluating-a-watch-expression.md)
