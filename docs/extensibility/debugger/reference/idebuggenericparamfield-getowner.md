---
title: IDebugGenericParamField::GetOwner | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericParamField::GetOwner
ms.assetid: c7f6d166-a69e-40c4-bd0b-1a1fdf9aaacf
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e78407f3398997e1369d71e9d3ab0dc0c7efd018
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericparamfieldgetowner"></a>IDebugGenericParamField::GetOwner
Récupère le propriétaire du type ou de méthode de ce paramètre générique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOwner(  
   IDebugField** ppOwner  
);  
```  
  
```csharp  
int GetOwner(  
   out IDebugField ppOwner  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppOwner`  
 [out] Retourne le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet qui possède ce paramètre générique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugGenericParamFieldType** objet qui expose la [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetOwner(IDebugField** ppOwner)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetOwner );  
  
    IfFalseGo(ppOwner, E_INVALIDARG );  
    *ppOwner = NULL;  
  
    IfFailGo( this->LoadProps() );  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
  
    switch (TypeFromToken(m_tokOwner))  
    {  
        case mdtMethodDef:  
            {  
                mdTypeDef tokClass;  
                CComPtr<IDebugField> pClass;  
                CDEBUG_ADDRESS caddr;  
                CComPtr<IDebugContainerField> pContainer;  
  
                IfFailGo( pMetadata->GetMethodProps( m_tokOwner, &tokClass, NULL, 0, NULL, NULL, NULL, NULL, NULL, NULL ) );  
                IfFailGo( m_spSH->CreateClassType(m_idModule, tokClass, &pClass) );  
                IfFailGo( pClass->QueryInterface( &pContainer ) );  
                IfFailGo( caddr.InitializeMethod( m_idModule, tokClass, m_tokOwner, 0, 0 ) );  
                IfFailGo( m_spSH->CreateMethodSymbol( pContainer, caddr, FIELD_SYM_MEMBER, ppOwner ) );  
                break;  
            }  
        case mdtTypeDef:  
            {  
                IfFailGo( m_spSH->CreateClassType(m_idModule, m_tokOwner, ppOwner) );  
                break;  
            }  
        default:  
            {  
                ASSERT(!"Unexpected Owner type for Generic Param Field");  
                hr = E_FAIL;  
            }  
    }  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetOwner, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)