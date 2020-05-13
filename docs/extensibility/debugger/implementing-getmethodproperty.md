---
title: Mise en œuvre de GetMethodProperty (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738514"
---
# <a name="implement-getmethodproperty"></a>Implémentez GetMethodProperty
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio appelle le moteur de débog (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), qui à son tour appelle [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir des informations sur la méthode actuelle sur le cadre de pile.

Cette mise `IDebugExpressionEvaluator::GetMethodProperty` en œuvre effectue les tâches suivantes :

1. Appels [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), en passant dans [l’objet IDebugAddress.](../../extensibility/debugger/reference/idebugaddress.md) Le fournisseur de symboles (SP) renvoie un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) représentant la méthode qui contient l’adresse spécifiée.

2. Obtient [l’IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField`de la .

3. Instantiates une classe `CFieldProperty` (appelée dans cet exemple) qui implémente [l’interface IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) et contient l’objet `IDebugMethodField` retourné du SP.

4. Retourne `IDebugProperty2` l’interface `CFieldProperty` de l’objet.

## <a name="managed-code"></a>Code managé
Cet exemple montre `IDebugExpressionEvaluator::GetMethodProperty` une implémentation de code géré.

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

## <a name="unmanaged-code"></a>Code non-gestion
Cet exemple montre `IDebugExpressionEvaluator::GetMethodProperty` une implémentation de code non menté.

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
- [Exemple de mise en œuvre des habitants](../../extensibility/debugger/sample-implementation-of-locals.md)
