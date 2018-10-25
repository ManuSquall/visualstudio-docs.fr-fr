---
title: IDebugGenericParamField::GetNameOfFormalParam | Microsoft Docs
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
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85c526f1764152ba66d9754b1b334d3637de7cc3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817572"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère le nom de ce paramètre générique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 [out] Nom de ce paramètre générique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugGenericParamFieldType** objet qui expose le [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

