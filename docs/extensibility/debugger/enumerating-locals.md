---
title: Énumération des variables locales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13dfa2ada2b0df38a133bb3f2bc112b496129f1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869910"
---
# <a name="enumerate-locals"></a>Énumérer des variables locales
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque Visual Studio est prêt remplir le **variables locales** fenêtre, elle appelle [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sur le [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet retourné à partir de [ GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) (consultez [implémentation de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren` Retourne un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet.  
  
 Implémentation `IDebugProperty2::EnumChildren` effectue les tâches suivantes :  
  
1.  Garantit que cela représente une méthode.  
  
2.  Utilise le `guidFilter` argument pour déterminer la méthode à appeler sur le [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objet. Si `guidFilter` est égal à :  
  
    1.  `guidFilterLocals`, appelez [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) pour obtenir un [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) objet.  
  
    2.  `guidFilterArgs`, appelez [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) pour obtenir un `IEnumDebugFields` objet.  
  
    3.  `guidFilterLocalsPlusArgs`, synthétiser une énumération qui combine les résultats de `IDebugMethodField::EnumLocals` et `IDebugMethodField::EnumArguments`. Cette synthèse est représentée par la classe `CEnumMethodField`.  
  
3.  Instancie une classe (appelée `CEnumPropertyInfo` dans cet exemple) qui implémente le `IEnumDebugPropertyInfo2` interface et contient le `IEnumDebugFields` objet.  
  
4.  Retourne le `IEnumDebugProperty2Info2` de l’interface à partir de la `CEnumPropertyInfo` objet.  
  
## <a name="managed-code"></a>Code managé  
 Cet exemple illustre une implémentation de `IDebugProperty2::EnumChildren` dans du code managé.  
  
```csharp  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT EnumChildren (  
                uint                    dwFields,  
                uint                    radix,  
            ref Guid                    guidFilter,   
                ulong                   attribFilter,   
                string                  nameFilter,   
                uint                    timeout,  
            out IEnumDebugPropertyInfo2 properties)   
        {  
            properties = null;  
            IEnumDebugFields fields = null;  
  
            // If this field is a method...  
            if (0 != ((uint) fieldKind & (uint) FIELD_KIND.FIELD_TYPE_METHOD))  
            {  
                IDebugMethodField methodField = (IDebugMethodField) field;  
  
                // Enumerate parameters.  
                if (guidFilter == FilterGuids.guidFilterArgs)  
                {  
                    methodField.EnumParameters(out fields);    
                }  
                // Enumerate local variables.  
                else if (guidFilter == FilterGuids.guidFilterLocals)  
                {  
                    methodField.EnumLocals(address, out fields);    
                }  
                // Enumerate all local variables, including invisible compiler temps.  
                else if (guidFilter == FilterGuids.guidFilterAllLocals)  
                {  
                    methodField.EnumAllLocals(address, out fields);    
                }  
                // Enumerate "this", if any, and all parameters and local variables.  
                else if (guidFilter == FilterGuids.guidFilterLocalsPlusArgs)  
                {  
                    IDebugClassField fieldThis   = null;  
                    IEnumDebugFields parameters = null;  
                    IEnumDebugFields locals     = null;  
  
                    methodField.GetThis(out fieldThis);  
                    methodField.EnumParameters(out parameters);  
                    methodField.EnumLocals(address, out locals);  
  
                    CEnumMethodField enumMethodField =   
                        new CEnumMethodField(fieldThis, parameters, locals);  
                    fields = (IEnumDebugFields) enumMethodField;  
                }  
                // Enumerate only "this".  
                else if (guidFilter == FilterGuids.guidFilterThis)  
                {  
                    IDebugClassField fieldThis   = null;  
                    methodField.GetThis(out fieldThis);  
  
                    CEnumMethodField enumMethodField =   
                        new CEnumMethodField(fieldThis, null, null);  
                    fields = (IEnumDebugFields) enumMethodField;  
                }  
                else throw new COMException();// E_FAIL  
            }  
            // Wrap a property enumerator around the field enumerator.  
            CEnumPropertyInfo propertiesInfo =   
                new CEnumPropertyInfo(provider, address, binder, radix, fields,   
                 (DEBUGPROP_INFO_FLAGS) dwFields);  
  
            properties = (IEnumDebugPropertyInfo2) propertiesInfo;  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Code non managé  
 Cet exemple illustre une implémentation de `IDebugProperty2::EnumChildren` en code non managé.  
  
```cpp  
STDMETHODIMP CFieldProperty::EnumChildren(   
        in DEBUGPROP_INFO_FLAGS        infoFlags,  
        in DWORD                       radix,  
        in REFGUID                     guidFilter,  
        in DBG_ATTRIB_FLAGS            attribFilter,  
        in LPCOLESTR                   pszNameFilter,  
        in DWORD                       timeout,  
        out IEnumDebugPropertyInfo2 ** ppchildren )  
{  
    if (ppchildren == NULL)  
        return E_INVALIDARG;  
    else  
        *ppchildren = 0;  
  
    //get enumeration  
    HRESULT hr;  
    IEnumDebugFields*     pfields    = NULL;  
  
    if (m_fieldKind & FIELD_TYPE_METHOD)  
    {  
        //-----------------------------------------------------  
        // A Method  
  
        IDebugMethodField*  pmethod    = NULL;  
  
        //enumerate the requested properties  
        hr = m_field->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod) );  
        if (FAILED(hr))  
            return hr;  
  
        if (guidFilter == guidFilterArgs)  
        {  
            hr = pmethod->EnumParameters( &pfields );    
        }  
        else if (guidFilter == guidFilterLocals)  
        {  
            hr = pmethod->EnumLocals( m_address, &pfields );  
        }  
        else if (guidFilter == guidFilterAllLocals)  
        {  
            hr = pmethod->EnumAllLocals( m_address, &pfields );  
        }  
        else if (guidFilter == guidFilterLocalsPlusArgs)  
        {  
            //we create a special enumerator for this  
            IDebugClassField* pfieldThis  = NULL;  
            IEnumDebugFields* pparameters = NULL;  
            IEnumDebugFields* plocals     = NULL;  
  
            pmethod->GetThis( &pfieldThis );  
            pmethod->EnumParameters( &pparameters );  
            pmethod->EnumLocals( m_address, &plocals );  
  
            CEnumMethodField* penumMethodField =  
                new CEnumMethodField( pfieldThis, pparameters, plocals );  
            if (pfieldThis != NULL)  
                pfieldThis->Release();  
            if (pparameters != NULL)  
                pparameters->Release();  
            if (plocals != NULL)  
                plocals->Release();  
            if (!penumMethodField)   
            {   
                hr = E_OUTOFMEMORY;  
            }  
            else  
            {  
                hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,  
                        reinterpret_cast<void**>(&pfields) );  
                penumMethodField->Release();  
            }  
        }  
        else if (guidFilter == guidFilterThis )  
        {  
            IDebugClassField* pfieldThis  = NULL;  
  
            hr = pmethod->GetThis( &pfieldThis );  
            if (SUCCEEDED(hr))  
            {  
                CEnumMethodField* penumMethodField =  
                    new CEnumMethodField( pfieldThis, NULL, NULL );  
                pfieldThis->Release();  
                if (!penumMethodField)   
                {  
                    hr = E_OUTOFMEMORY;  
                }  
                else  
                {  
                    hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,  
                        reinterpret_cast<void**>(&pfields) );  
                    penumMethodField->Release();  
                }  
            }  
        }  
        else  
        {  
            hr = E_FAIL;  
        }  
  
        pmethod->Release();  
        if (hr != S_OK)  
            return hr;  
    }  
  
    //create a property info enumeration around the field enumerator  
    CEnumPropertyInfo* pproperties =  
        new CEnumPropertyInfo( m_provider, m_address, m_binder,   
                               radix, pfields, infoFlags );  
    if (pfields != NULL)  
        pfields->Release();  
    if (pproperties == NULL)  
        return E_OUTOFMEMORY;  
  
    hr = pproperties->QueryInterface( IID_IEnumDebugPropertyInfo2,  
        reinterpret_cast<void**>(ppchildren) );  
    pproperties->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’implémentation des variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Implémentation de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)   
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)