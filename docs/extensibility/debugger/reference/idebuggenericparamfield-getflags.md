---
title: "IDebugGenericParamField::GetFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFlags"
  - "IDebugGenericParamField::GetFlags"
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère les balises pour ce paramètre générique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```c#  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### Paramètres  
 `pdwFlags`  
 \[out\]  Retourne les balises pour ce paramètre générique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Ces indicateurs contiennent des informations sur les différentes contraintes spéciales.  
  
## Exemple  
 L'exemple de code suivant montre comment appliquer cette méthode d'un objet **de CDebugGenericParamFieldType** qui expose l'interface d' [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)