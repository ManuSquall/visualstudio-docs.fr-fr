---
title: IDebugCustomAttributeQuery::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ff58df26391c3c3fe312f9268f905b4f4f15b858
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "62538201"
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère un attribut personnalisé est fonction de son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
```cpp#  
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
