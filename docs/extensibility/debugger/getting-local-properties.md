---
title: Obtention des propriétés locales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 040b40b5990edbfbd99c240d8b7e2d02e59c33af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925629"
---
# <a name="get-local-properties"></a>Obtenir les propriétés locales
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Les appels de Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet qui fournit l’accès à toutes les variables locales à afficher dans le **variables locales** fenêtre. Visual Studio appelle ensuite [suivant](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) pour obtenir les informations à afficher pour chaque local. Dans cet exemple, la classe `CEnumPropertyInfo` implémente le `IEnumDebugPropertyInfo2` interface.

Cette implémentation de `IEnumDebugPropertyInfo2::Next` effectue les tâches suivantes :

1. Efface le tableau dans lequel les informations désignant être stocké.

2. Appels [suivant](../../extensibility/debugger/reference/ienumdebugfields-next.md) pour chaque ordinateur local, stockage retourné [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) dans le tableau à retourner. Le [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) objet a été fourni lorsque cela `CEnumPropertyInfo` classe a été instanciée.

## <a name="managed-code"></a>Code managé
Cet exemple illustre une implémentation de `IEnumDebugPropertyInfo2::EnumChildren` pour les variables locales d’une méthode dans le code managé.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Code non managé
 Cet exemple illustre une implémentation de `IEnumDebugPropertyInfo2::EnumChildren` pour les variables locales d’une méthode en code non managé.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [Exemple d’implémentation des variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Énumération des variables locales](../../extensibility/debugger/enumerating-locals.md)
