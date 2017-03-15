---
title: "Exemple d&#39;impl&#233;mentation de l&#39;&#233;valuation d&#39;Expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluateurs d'expression"
  - "débogage des évaluateurs d'expression [Debugging SDK],"
  - "évaluation d'expression, exemples"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Exemple d&#39;impl&#233;mentation de l&#39;&#233;valuation d&#39;Expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d'implémenter des évaluateurs d'expression est déconseillée. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez [évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d'évaluateur d'Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour un **Espion** expression de la fenêtre, Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour produire un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet.`IDebugExpressionContext2::ParseText` instancie un évaluateur d'expression \(EE\) et appelle [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
 Cette implémentation de `IDebugExpressionEvaluator::Parse` effectue les tâches suivantes :  
  
1.  \(C\+\+ uniquement\) Analyse de l'expression pour rechercher des erreurs.  
  
2.  Instancie une classe \(appelée `CParsedExpression` dans cet exemple\) qui implémente le `IDebugParsedExpression` de l'interface et le stocke dans la classe de l'expression doit être analysé.  
  
3.  Retourne le `IDebugParsedExpression` de l'interface à partir de la `CParsedExpression` objet.  
  
> [!NOTE]
>  Dans les exemples qui suivent et dans l'exemple MyCEE, l'évaluateur d'expression ne sépare pas l'analyse de l'évaluation.  
  
## Code managé  
 Il s'agit d'une implémentation de `IDebugExpressionEvaluator::Parse` dans le code managé. Notez que cette version de la méthode diffère de l'analyse à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que le code d'analyse prend également en même temps \(voir [L'évaluation d'une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## Code non managé  
 Il s'agit d'une implémentation de `IDebugExpressionEvaluator::Parse` en code non managé. Cette méthode appelle une fonction d'assistance, `Parse`, d'analyser l'expression et recherchez des erreurs, mais cette méthode ignore la valeur résultante. L'évaluation formelle est différée à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) où l'expression est analysée pendant son évaluation \(voir [L'évaluation d'une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## Voir aussi  
 [Évaluation d'une Expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [L'évaluation d'une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)