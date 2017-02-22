---
title: "IDebugGenericParamField::GetNameOfFormalParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField::GetNameOfFormalParam"
  - "GetNameOfFormalParam"
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetNameOfFormalParam
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait le nom de ce paramètre générique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  nom de ce paramètre générique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugGenericParamFieldType** qui expose l'interface d' [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrName;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)