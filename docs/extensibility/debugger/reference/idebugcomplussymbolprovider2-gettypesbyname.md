---
title: "IDebugComPlusSymbolProvider2::GetTypesByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypesByName"
  - "IDebugComPlusSymbolProvider2::GetTypesByName"
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider2::GetTypesByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère un type en fonction de son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetTypesByName(  
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetTypesByName(  
   string               pszClassName,  
   enum_ NAME_MATCH     nameMatch,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszClassName`  
 [in] Nom du type.  
  
 `nameMatch`  
 [in] Sélectionne le type de correspondance, par exemple, qui respecte la casse. Une valeur à partir de la [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) (énumération).  
  
 `ppEnum`  
 [out] Énumérateur qui contient l’ou les types portant le nom spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour les types génériques, le nom à rechercher pour « liste \< int>» ou « List \< int, int > » serait « List ». Si les types du même nom apparaissent dans plusieurs modules, la `ppEnum` paramètre contiendra toutes les copies. Vous devez utiliser [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) et distinguer en fonction de le `guidModule` paramètre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose les [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypesByName(  
    LPCOLESTR pszClassName,  
    NAME_MATCH nameMatch,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CModIter ModIter;  
    CModule* pmodule; // the iterator owns the reference  
    CFieldList listField;  
  
    ASSERT(IsValidWideStringPtr(pszClassName));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );  
  
    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    hr = S_FALSE;  
  
    if ( nameMatch == nmCaseInsensitive)  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,  
                    &listField,  
                    this ) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
    else  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByName( pszClassName,  
                                          &listField,  
                                          this) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
  
    // If the list is empty then no type  
    IfFalseGo( listField.GetCount(), E_FAIL );  
  
    // Create enumerator  
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)