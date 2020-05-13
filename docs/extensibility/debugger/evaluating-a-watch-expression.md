---
title: Évaluation d’une expression de montre (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738857"
---
# <a name="evaluate-a-watch-expression"></a>Évaluer l’expression d’une montre
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Lorsque Visual Studio est prêt à afficher la valeur d’une expression de montre, il appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), qui à son tour appelle [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Ce processus produit un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui contient la valeur et le type de l’expression.

Dans cette `IDebugParsedExpression::EvaluateSync`mise en œuvre de , l’expression est analysée et évaluée en même temps. Cette implémentation effectue les tâches suivantes :

1. Parse et évalue l’expression pour produire un objet générique qui détient la valeur et son type. Dans C, cela est représenté `object` comme un certain temps dans C `VARIANT`, cela est représenté comme un .

2. Instantanés une classe `CValueProperty` (appelée dans cet exemple) qui implémente l’interface `IDebugProperty2` et stocke dans la classe la valeur à retourner.

3. Retourne `IDebugProperty2` l’interface `CValueProperty` de l’objet.

## <a name="managed-code"></a>Code managé
Il s’agit `IDebugParsedExpression::EvaluateSync` d’une implémentation du code géré. La méthode `Tokenize` d’aide analyse l’expression dans un arbre d’analyse. La fonction `EvalToken` d’aide convertit le jeton à une valeur. La fonction `FindTerm` d’aide traverse de façon récursive l’arbre d’analyse, appelant `EvalToken` chaque nœud représentant une valeur et appliquant toutes les opérations (ajout ou soustraction) dans l’expression.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Code non-gestion
Il s’agit `IDebugParsedExpression::EvaluateSync` d’une implémentation du code non menté. La fonction `Evaluate` d’aide analyse et évalue l’expression, en retournant une `VARIANT` fixation de la valeur résultante. La fonction `VariantValueToProperty` d’aide `VARIANT` regroupe `CValueProperty` l’objet.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Voir aussi
- [Évaluer l’expression d’une fenêtre de montre](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Exemple de mise en œuvre de l’évaluation de l’expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
