---
title: "L’impl&#233;mentation de GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMethodProperty (méthode)"
  - "Propriété de IDebugExpressionEvaluator2"
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# L’impl&#233;mentation de GetMethodProperty
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio appelle le moteur de débogage \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), qui à son tour appelle [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir des informations sur la méthode en cours sur le frame de pile.  
  
 Cette implémentation de `IDebugExpressionEvaluator::GetMethodProperty` effectue les tâches suivantes :  
  
1.  Appels [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), en passant le [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) objet. Le fournisseur de symboles \(SP\) retourne un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) qui représente la méthode qui contient l’adresse spécifiée.  
  
2.  Obtient le [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) à partir de la `IDebugContainerField`.  
  
3.  Instancie une classe \(appelée `CFieldProperty` dans cet exemple\) qui implémente le [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) de l’interface et contient le `IDebugMethodField` objet retourné par le fournisseur de services.  
  
4.  Retourne le `IDebugProperty2` de l’interface à partir de la `CFieldProperty` objet.  
  
## Code managé  
 Cet exemple illustre une implémentation de `IDebugExpressionEvaluator::GetMethodProperty` dans le code managé.  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## Code non managé  
 Cet exemple illustre une implémentation de `IDebugExpressionEvaluator::GetMethodProperty` en code non managé.  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## Voir aussi  
 [Exemple d'implémentation des variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)