---
title: 'IDebugComPlusSymbolProvider :: GetTypeFromAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetTypeFromAddress
- GetTypeFromAddress
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3fc5548bd4c52dad5df058fdf86d1fab5ea460b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200569"
---
# <a name="idebugcomplussymbolprovidergettypefromaddress"></a>IDebugComPlusSymbolProvider::GetTypeFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère un type de symbole en fonction de son adresse de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetTypeFromAddress(  
   IDebugAddress* pAddress,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetTypeFromAddress(  
   IDebugAddress   pAddress,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 dans Adresse de débogage qui est représentée par une interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `ppField`  
 à Retourne le type de tableau tel qu’il est représenté par une interface [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugSymbolProvider** qui expose l’interface [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypeFromAddress(  
    IDebugAddress *pAddress,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
    CDEBUG_ADDRESS da;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromPrimitive );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    IfFailGo( pAddress->GetAddress(&da) );  
  
    switch ( da.addr.dwKind )  
    {  
        case ADDRESS_KIND_METADATA_LOCAL:  
        case ADDRESS_KIND_METADATA_PARAM:  
        case ADDRESS_KIND_METADATA_FIELD:  
        case ADDRESS_KIND_METADATA_ARRAYELEM:  
        case ADDRESS_KIND_METADATA_METHOD:  
            {  
                IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );  
                break;  
            }  
  
        case ADDRESS_KIND_METADATA_RETVAL:  
            {  
                if ( da.addr.addr.addrRetVal.dwCorType )  
                {  
  
                    IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );  
                    IfFailGo( this->CreateType((const COR_SIGNATURE*)(&da.addr.addr.addrRetVal.rgSig),  
                                               da.addr.addr.addrRetVal.dwSigSize,  
                                               da.GetModule(),  
                                               mdMethodDefNil,  
                                               pGenScope,  
                                               ppField) );  
                }  
                else  
                {  
                    IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );  
                }  
  
                break;  
            }  
  
        default:  
            {  
                ASSERT(!"Address type not supported.");  
            }  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromPrimitive, hr );  
  
    RELEASE( pGenScope );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
