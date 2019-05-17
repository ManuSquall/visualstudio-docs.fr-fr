---
title: Évaluer les variables locales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e31aa560422c9f18ec30a6e203559ef3ed10c52
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444771"
---
# <a name="evaluating-locals"></a>Évaluation des variables locales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) est appelée pour obtenir la valeur de local, ainsi que les nom de l’ordinateur local et le type. Dans la mesure où la valeur d’une variable locale est dépendante de l’état actuel du programme, la valeur de la locale doit être obtenue à partir de la mémoire. Le [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) objet est utilisé pour lier le [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet représentant l’ordinateur local vers l’emplacement approprié dans la mémoire contenant la valeur. Cet emplacement en mémoire est représenté par un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet.  
  
 Cette fonctionnalité de récupération de la valeur d’une variable locale est encapsulée dans une fonction d’assistance qui effectue les tâches suivantes :  
  
1. Lie le `IDebugField` objet vers la mémoire pour obtenir un `IDebugObject` objet.  
  
2. Obtient la valeur de la mémoire. Cette valeur est représentée comme une série d’octets.  
  
3. Met en forme la valeur basée sur type de l’ordinateur local.  
  
4. Retourne un objet générique qui contient la valeur de la locale. En c#, il s’agit d’un `object`, et en C++, il s’agit d’un `VARIANT`.  
  
## <a name="managed-code"></a>Code managé  
 Il s’agit d’une implémentation d’une fonction qui Récupère la valeur d’une variable locale dans le code managé.  
  
```csharp  
namespace EEMC  
{  
    internal class Field  
    {  
        internal static object GetValue(  
            IDebugBinder binder,  
            IDebugField field,  
            Type t,  
            uint size)  
        {  
            if (t == null || size == 0)  return null;  
  
            IDebugObject debugObject = null;  
            binder.Bind(null, field, out debugObject);  
  
            byte[] buffer = new byte[size];  
            for (int i = 0; i < size; i++)  buffer[i] = 0;  
  
            debugObject.GetValue(buffer, size);   
  
            if (t == typeof(sbyte)) return (sbyte) buffer[0];  
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);  
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);  
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);  
            if (t == typeof(byte))  return buffer[0];  
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);  
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);  
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);  
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);  
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);  
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);  
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);  
            return null;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Code non managé  
 Il s’agit d’une implémentation d’une fonction qui Récupère la valeur d’une variable locale dans le code non managé. `FieldGetType` est indiqué dans [l’obtention des valeurs locales](../../extensibility/debugger/getting-local-values.md).  
  
```cpp#  
HRESULT FieldGetPrimitiveValue(  
    in  IDebugBinder* pbinder,  
    in  IDebugField*  pfield,  
    out VARIANT*      pvarValue  
    )  
{  
    if (pvarValue == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarValue = 0;  
  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    UINT          valueSize = 0;  
    BYTE*         pvalueBits = NULL;  
    IDebugObject* pobject    = NULL;  
  
    //get the value as bits  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
        return hr;  
  
    hr = pobject->GetSize( &valueSize );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        return hr;  
    }  
  
    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));  
    if (!pvalueBits)  
    {  
        pobject->Release();  
        return E_OUTOFMEMORY;  
    }  
  
    hr = pobject->GetValue( pvalueBits, valueSize );  
    pobject->Release();  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //get the type  
    VARIANT     valueType;  
  
    hr = FieldGetType( pfield, &valueType );  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //copy a primitive value  
    switch (valueType.vt)  
    {  
    case VT_BSTR:  
        {  
            pvarValue->vt = VT_BSTR;  
            if (valueSize == 0)  
                pvarValue->bstrVal = SysAllocString( OLE("") );  
            else  
                pvarValue->bstrVal =  
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),  
                                           valueSize );  
        }  
  
    case VT_BOOL:  
    case VT_I1:  
    case VT_I2:  
    case VT_I4:  
    case VT_I8:  
    case VT_UI1:  
    case VT_UI2:  
    case VT_UI4:  
    case VT_UI8:  
    case VT_R4:  
    case VT_R8:  
        pvarValue->vt = valueType.vt;  
  
        if (valueSize > 8)  
            valueSize = 8;  
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );  
        break;  
  
    case VT_VOID:  
    case VT_EMPTY:  
        pvarValue->vt = valueType.vt;  
        break;  
  
    default:  
        //not a primitive type  
        VariantClear(&valueType);  
        free(pvalueBits);  
        return E_FAIL;  
    }  
  
    free(pvalueBits);  
    VariantClear(&valueType);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’implémentation des variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Obtention des valeurs locales](../../extensibility/debugger/getting-local-values.md)   
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)
