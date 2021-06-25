---
title: Exemple d’implémentation de l’évaluation d’expression | Microsoft Docs
description: Découvrez comment Visual Studio appelle ParseText pour produire un objet IDebugExpression2 pour une expression Windows Watch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902304"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemple d’implémentation de l’évaluation d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Pour une expression de fenêtre **Espion** , Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour produire un objet [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` instancie un évaluateur d’expression (EE) et appelle [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour récupérer un objet [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Effectue les tâches suivantes :

1. [C++ uniquement] Analyse l’expression pour rechercher des erreurs.

2. Instancie une classe (appelée `CParsedExpression` dans cet exemple) qui exécute l' `IDebugParsedExpression` interface et stocke dans la classe l’expression à analyser.

3. Retourne l' `IDebugParsedExpression` interface de l' `CParsedExpression` objet.

> [!NOTE]
> Dans les exemples qui suivent et dans l’exemple MyCEE, l’évaluateur d’expression ne sépare pas l’analyse de l’évaluation.

## <a name="managed-code"></a>Code managé
 Le code suivant illustre une implémentation de `IDebugExpressionEvaluator::Parse` dans du code managé. Cette version de la méthode diffère l’analyse de [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , car le code d’analyse est également évalué en même temps (consultez [évaluer une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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

## <a name="unmanaged-code"></a>Code non managé
Le code suivant est une implémentation de `IDebugExpressionEvaluator::Parse` dans du code non managé. Cette méthode appelle une fonction d’assistance, `Parse` , pour analyser l’expression et rechercher les erreurs, mais cette méthode ignore la valeur résultante. L’évaluation formelle est reportée à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) où l’expression est analysée pendant son évaluation (consultez [évaluer une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Évaluer une expression de Fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Évaluer une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)
