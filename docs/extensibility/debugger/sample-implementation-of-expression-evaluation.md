---
title: "Exemple d’implémentation de l’évaluation d’Expression | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2cae1e8d697ba8079b29fa2188f0fb2f8b9a40e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemple d’implémentation de l’évaluation d’Expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour un **espion** expression de la fenêtre, les appels de Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour produire un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet. `IDebugExpressionContext2::ParseText`instancie l’évaluateur d’expression (EE) et appelle [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
 Cette implémentation de `IDebugExpressionEvaluator::Parse` effectue les tâches suivantes :  
  
1.  (C++ uniquement) Analyse de l’expression pour rechercher des erreurs.  
  
2.  Instancie une classe (appelée `CParsedExpression` dans cet exemple) qui implémente le `IDebugParsedExpression` de l’interface et la stocke dans la classe de l’expression doit être analysé.  
  
3.  Retourne le `IDebugParsedExpression` de l’interface à partir de la `CParsedExpression` objet.  
  
> [!NOTE]
>  Dans les exemples qui suivent et dans l’exemple MyCEE, l’évaluateur d’expression ne sépare pas l’analyse de l’évaluation.  
  
## <a name="managed-code"></a>Code managé  
 Il s’agit d’une implémentation de `IDebugExpressionEvaluator::Parse` dans le code managé. Notez que cette version de la méthode diffère de l’analyse à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) comme le code d’analyse évalue également en même temps (consultez [l’évaluation d’une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Il s’agit d’une implémentation de `IDebugExpressionEvaluator::Parse` en code non managé. Cette méthode appelle une fonction d’assistance, `Parse`, d’analyser l’expression et recherchez les erreurs, mais cette méthode ignore la valeur obtenue. L’évaluation formelle est soumise à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) où l’expression est analysée pendant qu’elle est évaluée (consultez [l’évaluation d’une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 [L’évaluation d’une Expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Évaluation d’une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)