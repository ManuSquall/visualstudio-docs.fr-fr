---
title: "IDebugBeforeSymbolSearchEvent2::GetModuleName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetModuleName"
  - "IDebugBeforeSymbolSearchEvent2::GetModuleName"
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugBeforeSymbolSearchEvent2::GetModuleName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait le nom du module actuellement en cours de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetModuleName(   
   BSTR *pbstrModuleName  
);  
```  
  
```c#  
public int GetModuleName (  
   string pbstrModuleName  
);  
```  
  
#### Paramètres  
 `pbstrModuleName`  
 \[out\]  nom du module.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugBeforeSymbolSearchEventBase** qui expose l'interface d' [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) .  
  
```cpp#  
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (m_bstrModuleName)  
    {  
  
        *pbstrModuleName = SysAllocString( m_bstrModuleName);  
  
        if (*pbstrModuleName)  
        {  
            hRes = S_OK;  
        }  
    }  
  
    return ( hRes );  
}  
```  
  
## Voir aussi  
 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)