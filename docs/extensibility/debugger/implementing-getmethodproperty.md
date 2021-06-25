---
title: Implémentation de GetMethodProperty | Microsoft Docs
description: Découvrez comment Visual Studio obtient des informations sur la méthode actuelle sur le frame de pile à l’aide du GetDebugProperty du moteur de débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab7b0ba5e51ba8ea47b473934e825b82dec320c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903292"
---
# <a name="implement-getmethodproperty"></a>Implémenter GetMethodProperty
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio appelle le moteur de débogage (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), qui à son tour appelle [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir des informations sur la méthode actuelle sur le frame de pile.

Cette implémentation de `IDebugExpressionEvaluator::GetMethodProperty` effectue les tâches suivantes :

1. Appelle [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), en passant l’objet [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) . Le fournisseur de symboles (SP) retourne un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) représentant la méthode qui contient l’adresse spécifiée.

2. Obtient le [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) à partir du `IDebugContainerField` .

3. Instancie une classe (appelée `CFieldProperty` dans cet exemple) qui implémente l’interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) et contient l' `IDebugMethodField` objet retourné par le SP.

4. Retourne l' `IDebugProperty2` interface de l' `CFieldProperty` objet.

## <a name="managed-code"></a>Code managé
Cet exemple illustre une implémentation de `IDebugExpressionEvaluator::GetMethodProperty` dans du code managé.

```csharp
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

## <a name="unmanaged-code"></a>Code non managé
Cet exemple illustre une implémentation de `IDebugExpressionEvaluator::GetMethodProperty` dans du code non managé.

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

## <a name="see-also"></a>Voir aussi
- [Exemple d’implémentation de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)
