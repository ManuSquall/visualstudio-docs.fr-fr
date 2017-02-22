---
title: "IDebugBoundBreakpoint2::GetBreakpointResolution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetBreakpointResolution"
helpviewer_keywords: 
  - "GetBreakpointResolution (méthode)"
  - "IDebugBoundBreakpoint2::GetBreakpointResolution (méthode)"
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetBreakpointResolution
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la résolution de point d'arrêt qui décrit ce point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```c#  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### Paramètres  
 `ppBPResolution`  
 \[out\]  Retourne l'interface d' [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) qui représente un des éléments suivants :  
  
-   L'objet de résolution de point d'arrêt qui décrit l'emplacement dans le code où un point d'arrêt de code a été lié.  
  
-   La colocalisation des données pour lequel un point d'arrêt est lié.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si l'état de l'objet de point d'arrêt lié est défini à `BPS_DELETED` \(une partie de l'énumération de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Notes  
 Appelez la méthode d' [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) pour déterminer si la résolution de point d'arrêt est pour le code ou des données.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CBoundBreakpoint` qui expose l'interface d' [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
```  
HRESULT CBoundBreakpoint::GetBreakpointResolution(  
    IDebugBreakpointResolution2** ppBPResolution)  
{    
   HRESULT hr;    
  
   if (ppBPResolution)    
   {    
      // Verify that the bound breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugBreakpointResolution2 interface.    
         hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,  
                                       (void **)ppBPResolution);  
         assert(hr == S_OK);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
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
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)