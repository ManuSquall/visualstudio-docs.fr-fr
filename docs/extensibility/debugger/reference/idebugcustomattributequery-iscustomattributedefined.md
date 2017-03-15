---
title: "IDebugCustomAttributeQuery::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery::IsCustomAttributeDefined"
  - "IsCustomAttributeDefined"
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttributeQuery::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si l'attribut personnalisé spécifié est défini.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsCustomAttributeDefined(  
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   string pszCustomAttributeName  
);  
```  
  
#### Paramètres  
 `pszCustomAttributeName`  
 \[in\]  nom de l'attribut personnalisé.  
  
## Valeur de retour  
 Si l'attribut personnalisé est défini, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## Exemple  
 L'exemple de code suivant montre comment appliquer cette méthode d'un objet **de CDebugClassFieldSymbol** qui expose l'interface d' [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md) .  
  
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
  
## Voir aussi  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)