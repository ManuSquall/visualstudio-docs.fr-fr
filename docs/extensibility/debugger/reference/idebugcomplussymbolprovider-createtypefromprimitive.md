---
title: "IDebugComPlusSymbolProvider::CreateTypeFromPrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::CreateTypeFromPrimitive"
  - "CreateTypeFromPrimitive"
ms.assetid: 37213cc2-a038-42ea-9b28-3ae40d4cfe69
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un type à partir du type primitif spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT CreateTypeFromPrimitive(  
   DWORD          dwPrimType,  
   IDebugAddress* pAddress,  
   IDebugField**  ppType  
);  
```  
  
```  
[C#]  
int CreateTypeFromPrimitive(  
   uint          dwPrimType,  
   IDebugAddress pAddress,  
   IDebugField   ppType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwPrimType`  
 [in] Valeur de la [CorElementType, énumération](CorElementType%20Enumeration.xml) qui représente le type primitif.  
  
 `pAddress`  
 [in] Un type d’objet représenté par une [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `ppType`  
 [in] Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui décrit le type d’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose les [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::CreateTypeFromPrimitive(  
    DWORD dwPrimType,  
    IDebugAddress* pAddress,  
    IDebugField** ppType)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS addr;  
    const COR_SIGNATURE* pTypeInfo = (const COR_SIGNATURE*) & dwPrimType;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    //  
    // This function will only work for primitive types  
    //  
  
    METHOD_ENTRY( CDebugSymbolProvider::CreateTypeFromPrimitive );  
  
    IfFailGo( pAddress->GetAddress( &addr ) );  
  
    IfNullGo( pGenScope = new CDebugGenericParamScope(addr.GetModule(), addr.tokClass, addr.GetMethod()), E_OUTOFMEMORY );  
  
    IfFailGo( CreateType( pTypeInfo,  
                          1,  
                          addr.GetModule(),  
                          addr.GetMethod(),  
                          pGenScope,  
                          ppType ) );  
  
    METHOD_EXIT( CDebugSymbolProvider::CreateTypeFromPrimitive, hr );  
  
Error:  
  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)