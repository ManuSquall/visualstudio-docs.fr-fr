---
title: "IDebugComPlusSymbolProvider::IsHiddenCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::IsHiddenCode"
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider::IsHiddenCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détermine si le code à l'adresse spécifiée de débogueur est masqué.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsHiddenCode(  
   IDebugAddress* pAddress  
);  
```  
  
```c#  
int IsHiddenCode(  
   IDebugAddress pAddress  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  l'adresse de débogage qui est représentée par une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Valeur de retour  
 Si le code est masqué, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugSymbolProvider** qui expose l'interface d' [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsHiddenCode(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,  
                                address.addr.addr.addrMethod.dwVersion,  
                                address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this sequence point is not hidden  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)