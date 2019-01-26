---
title: L’évaluation d’une Expression espionne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df014b855528fa0c86ab83b608d77ab4b0797edf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070589"
---
# <a name="evaluate-a-watch-expression"></a>Évaluer une expression espionne
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque Visual Studio est prêt à afficher la valeur d’une expression espionne, il appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), qui appelle à son tour [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Ce processus génère une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui contient la valeur et le type de l’expression.  
  
 Dans cette implémentation de `IDebugParsedExpression::EvaluateSync`, l’expression est analysée et évaluée en même temps. Cette implémentation effectue les tâches suivantes :  
  
1.  Analyse et évalue l’expression pour produire un objet générique qui contient la valeur et son type. Dans c#, ceci est représenté comme un `object` alors qu’en C++, cela est représenté comme un `VARIANT`.  
  
2.  Instancie une classe (appelée `CValueProperty` dans cet exemple) qui implémente le `IDebugProperty2` de l’interface et la stocke dans la classe de la valeur à retourner.  
  
3.  Retourne le `IDebugProperty2` de l’interface à partir de la `CValueProperty` objet.  
  
## <a name="managed-code"></a>Code managé  
 Il s’agit d’une implémentation de la `IDebugParsedExpression::EvaluateSync` dans du code managé. La méthode d’assistance `Tokenize` analyse l’expression dans une arborescence d’analyse. La fonction d’assistance `EvalToken` convertit le jeton à une valeur. La fonction d’assistance `FindTerm` récursivement parcourt l’arborescence d’analyse, l’appel `EvalToken` pour chaque nœud qui représente une valeur et en appliquant toutes les opérations (addition ou multiplication) dans l’expression.  
  
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
  
## <a name="unmanaged-code"></a>Code non managé  
 Il s’agit d’une implémentation de la `IDebugParsedExpression::EvaluateSync` en code non managé. La fonction d’assistance `Evaluate` analyse et évalue l’expression, en retournant un `VARIANT` contenant la valeur résultante. La fonction d’assistance `VariantValueToProperty` FAISCEAUX le `VARIANT` dans un `CValueProperty` objet.  
  
```cpp  
[C++]  
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
 [Évaluer une expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Exemple d’implémentation de l’évaluation d’expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)