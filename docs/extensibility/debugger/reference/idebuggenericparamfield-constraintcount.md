---
title: "IDebugGenericParamField::ConstraintCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstraintCount"
  - "IDebugGenericParamField::ConstraintCount"
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugGenericParamField::ConstraintCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le nombre de contraintes qui sont associées à ce paramètre générique.  
  
## Syntaxe  
  
```cpp#  
HRESULT ConstraintCount(  
   ULONG32* pcConst  
);  
```  
  
```c#  
int ConstraintCount(  
   ref uint pcConst  
);  
```  
  
#### Paramètres  
 `pcConst`  
 \[in, out\]  Numéro de contraintes qui sont associées à ce champ.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugGenericParamFieldType** qui expose l'interface d' [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<IMetaDataImport2> pMetadata2;  
    HCORENUM hEnum = 0;  
    ULONG cConst = 0;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );  
  
    IfFalseGo(pcConst, E_INVALIDARG );  
    *pcConst = 0;  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );  
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,  
              m_tokParam,  
              NULL,  
              0,  
              &cConst) );  
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );  
    pMetadata->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    *pcConst = cConst;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)