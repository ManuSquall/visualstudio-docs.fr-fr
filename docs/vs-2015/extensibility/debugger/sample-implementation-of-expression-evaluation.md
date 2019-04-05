---
title: Exemple d’implémentation de l’évaluation de l’Expression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb36540aaf6fa30cdcd069fd96a18124daafe2b8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948486"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemple d’implémentation de l’évaluation d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour un **espion** expression de la fenêtre, les appels de Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour produire un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet. `IDebugExpressionContext2::ParseText` instancie un évaluateur d’expression (EE) et appelle [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
 Cette implémentation de `IDebugExpressionEvaluator::Parse` effectue les tâches suivantes :  
  
1.  (C++ uniquement) Analyse l’expression pour rechercher des erreurs.  
  
2.  Instancie une classe (appelée `CParsedExpression` dans cet exemple) qui implémente le `IDebugParsedExpression` de l’interface et la stocke dans la classe de l’expression à analyser.  
  
3.  Retourne le `IDebugParsedExpression` de l’interface à partir de la `CParsedExpression` objet.  
  
> [!NOTE]
>  Dans les exemples qui suivent et dans l’exemple MyCEE, l’évaluateur d’expression ne sépare pas l’analyse de l’évaluation.  
  
## <a name="managed-code"></a>Code managé  
 Il s’agit d’une implémentation de `IDebugExpressionEvaluator::Parse` dans du code managé. Notez que cette version de la méthode diffère de l’analyse à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) comme le code pour l’analyse évalue également en même temps (voir [l’évaluation d’une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Il s’agit d’une implémentation de `IDebugExpressionEvaluator::Parse` en code non managé. Cette méthode appelle une fonction d’assistance, `Parse`, pour analyser l’expression et recherchez les erreurs, mais cette méthode ignore la valeur résultante. L’évaluation formelle est différée jusqu'à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) où l’expression est analysée pendant qu’il est évalué (consultez [l’évaluation d’une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
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
 [Évaluation d’une Expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Évaluation d’une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)
