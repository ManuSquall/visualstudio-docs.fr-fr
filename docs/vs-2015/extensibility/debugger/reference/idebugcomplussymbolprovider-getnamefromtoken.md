---
title: IDebugComPlusSymbolProvider::GetNameFromToken | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetNameFromToken
- GetNameFromToken
ms.assetid: 6e8cf468-5fd1-4655-93ed-88828d6068b7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4928510369c11ff7e3fb530c9206dbd5239e63a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852646"
---
# <a name="idebugcomplussymbolprovidergetnamefromtoken"></a>IDebugComPlusSymbolProvider::GetNameFromToken
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne le nom associé au jeton spécifié son objet de métadonnées spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetNameFromToken (  
   IUnknown* pMetadataImport,  
   DWORD     dwToken,  
   BSTR*     pbstrName  
);  
```  
  
```csharp  
int GetNameFromToken (  
   object     pMetadataImport,  
   uint       dwToken,  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMetadataImport`  
 [in] Objet qui contient les informations de métadonnées.  
  
 `dwToken`  
 [in] Jeton à nommer.  
  
 `pbstrName`  
 [out] Nom qui correspond au jeton.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetNameFromToken(  
    IUnknown* pMetadataImport,  
    DWORD dwToken,  
    BSTR* pbstrName  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetaData;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetNameFromToken);  
  
    IfFalseGo( pMetadataImport && pbstrName, E_INVALIDARG );  
  
    *pbstrName = NULL;  
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**) &pMetaData ) );  
  
    switch ( TypeFromToken(dwToken) )  
    {  
        case mdtModule:  
            IfFailGo( GetModuleName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtTypeDef:  
            IfFailGo( GetTypeName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtFieldDef:  
            IfFailGo( GetFieldName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtMethodDef:  
            IfFailGo( GetMethodName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtEvent:  
            IfFailGo( GetEventName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtProperty:  
            IfFailGo( GetPropertyName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        case mdtAssembly:  
            IfFailGo( GetAssemblyName( pMetaData, dwToken, pbstrName) );  
            break;  
  
        default:  
            ASSERT(!"Unsupported token passed to GetNameFromToken");  
            hr = E_FAIL;  
            break;  
    }  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetNameFromToken, hr);  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

