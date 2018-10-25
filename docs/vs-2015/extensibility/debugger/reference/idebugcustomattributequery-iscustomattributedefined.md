---
title: IDebugCustomAttributeQuery::IsCustomAttributeDefined | Microsoft Docs
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
- IDebugCustomAttributeQuery::IsCustomAttributeDefined
- IsCustomAttributeDefined
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac85bb50da04eeb53f63ec2561caf8fed55c52f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839464"
---
# <a name="idebugcustomattributequeryiscustomattributedefined"></a>IDebugCustomAttributeQuery::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si l’attribut personnalisé spécifié est défini.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsCustomAttributeDefined(  
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCustomAttributeName`  
 [in] Nom de l’attribut personnalisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Si l’attribut personnalisé est défini, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugClassFieldSymbol** objet qui expose le [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md) interface.  
  
```cpp#  
HRESULT CDebugClassFieldSymbol::IsCustomAttributeDefined(  
    LPCOLESTR pszCustomAttribute  
)  
{  
    HRESULT hr = S_FALSE;  
    CComPtr<IMetaDataImport> pMetadata;  
    mdToken token = mdTokenNil;  
    CComPtr<IDebugField> pField;  
    CComPtr<IDebugCustomAttributeQuery> pCA;  
  
    ASSERT(IsValidWideStringPtr(pszCustomAttribute));  
  
    METHOD_ENTRY( CDebugClassFieldSymbol::IsCustomAttributeDefined );  
  
    IfFalseGo( pszCustomAttribute, E_INVALIDARG );  
  
    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );  
  
    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );  
    IfFailGo( pMetadata->GetCustomAttributeByName( token,  
              pszCustomAttribute,  
              NULL,  
              NULL ) );  
Error:  
  
    METHOD_EXIT( CDebugClassFieldSymbol::IsCustomAttributeDefined, hr );  
  
    if (hr != S_OK)  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)

