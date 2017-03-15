---
title: "IDebugComPlusSymbolProvider::GetTypeFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::GetTypeFromAddress"
  - "GetTypeFromAddress"
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider::GetTypeFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait au symbole un type donné son adresse de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetTypeFromAddress(  
   IDebugAddress* pAddress,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetTypeFromAddress(  
   IDebugAddress   pAddress,  
   out IDebugField ppField  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  l'adresse de débogage qui est représentée par une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `ppField`  
 \[out\]  Retourne le type tableau à mesure qu'il est représenté par une interface d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugSymbolProvider** qui expose l'interface d' [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
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
  
## Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)