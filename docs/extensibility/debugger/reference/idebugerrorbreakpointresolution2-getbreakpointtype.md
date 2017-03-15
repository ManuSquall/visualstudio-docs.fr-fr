---
title: "IDebugErrorBreakpointResolution2::GetBreakpointType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpointResolution2::GetBreakpointType"
helpviewer_keywords: 
  - "IDebugErrorBreakpointResolution2::GetBreakpointType"
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le type de point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```c#  
int GetBreakpointType(   
   out enum_BP_TYPE pBPType  
);  
```  
  
#### Paramètres  
 `pBPType`  
 \[out\]  Retourne une valeur de l'énumération de [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) qui décrit le type de point d'arrêt.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode retourne le type du point d'arrêt qui ne l'a pas lié, et qui nécessitent un événement point d'arrêt d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CDebugErrorBreakpointResolution` qui expose l'interface d' [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) .  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.    
      if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)