---
title: IDebugGenericParamField::GetOwner | Microsoft Docs
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
- IDebugGenericParamField::GetOwner
ms.assetid: c7f6d166-a69e-40c4-bd0b-1a1fdf9aaacf
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f616030516794fcc4de805ed9add94753e2bc5f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759196"
---
# <a name="idebuggenericparamfieldgetowner"></a>IDebugGenericParamField::GetOwner
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère le type ou la méthode le propriétaire de ce paramètre générique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [out] Retourne le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet propriétaire de ce paramètre générique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugGenericParamFieldType** objet qui expose le [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
```cpp#  
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

