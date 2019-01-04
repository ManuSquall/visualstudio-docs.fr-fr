---
title: IDebugCustomAttributeQuery::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d82e650a1254635719cc663a6dab14456952084
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912569"
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
Récupère un attribut personnalisé est fonction de son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeByName(  
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   string    pszCustomAttributeName,  
   ref int[] ppBlob,  
   out uint  pdwLen  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCustomAttributeName`  
 [in] Nom de l’attribut personnalisé.  
  
 `ppBlob`  
 [in, out] Tableau d’octets qui contient les données d’attribut personnalisé.  
  
 `pdwLen`  
 [out] Longueur en octets de la `ppBlob` paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Si l’attribut personnalisé n’existe pas, retourne `S_FALSE`. Sinon, retourne un code d'erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugClassFieldSymbol** objet qui expose le [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md) interface.  
  
```cpp  
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(  
    LPCOLESTR pszCustomAttributeName,  
    BYTE *pBlob,  
    DWORD *pdwLen  
)  
{  
    HRESULT hr = S_FALSE;  
    CComPtr<IMetaDataImport> pMetadata;  
    mdToken token = mdTokenNil;  
    CComPtr<IDebugField> pField;  
    CComPtr<IDebugCustomAttributeQuery> pCA;  
  
    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));  
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));  
  
    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );  
  
    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );  
  
    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );  
  
    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );  
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,  
              token,  
              pszCustomAttributeName,  
              pBlob,  
              pdwLen ) );  
Error:  
  
    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)