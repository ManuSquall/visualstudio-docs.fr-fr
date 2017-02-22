---
title: "IDebugBoundBreakpoint2::Enable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::Enable"
helpviewer_keywords: 
  - "Enable (méthode)"
  - "IDebugBoundBreakpoint2::Enable (méthode)"
ms.assetid: 1b4e3f73-c94d-4aa3-9aa8-0d8cb8a6c5ca
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugBoundBreakpoint2::Enable
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

active ou désactive le point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT Enable(   
   BOOL fEnable  
);  
```  
  
```c#  
int Enable(   
   int fEnable  
);  
```  
  
#### Paramètres  
 `fEnable`  
 \[in\]  Affectez à la valeur est différente de zéro \(`TRUE`\) pour vérifier ou à zéro \(`FALSE`\) pour désactiver le point d'arrêt.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si l'état de l'objet de point d'arrêt lié est défini à `BPS_DELETED` \(une partie de l'énumération de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CBoundBreakpoint` qui expose l'interface d' [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
```  
HRESULT CBoundBreakpoint::Enable(BOOL fEnable)    
{    
   HRESULT hr;    
  
   // Verify that the bound breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state != BPS_DELETED)    
   {    
      // Check the state of the bound breakpoint. If the breakpoint is  
      // supposed to be, but has not already been, enabled, then have the  
      // interpreter set the breakpoint.    
      if (fEnable && m_state != BPS_ENABLED)    
      {    
         hr = m_pInterp->SetBreakpoint(m_sbstrDoc, this);    
         if (hr == S_OK)    
         {    
            // Change the state of the breakpoint to BPS_ENABLED.    
            m_state = BPS_ENABLED;    
         }    
      }    
      // Check the state of the bound breakpoint. If the breakpoint is   
      // supposed to be, but has not already been, disabled, then have the   
      // interpreter remove the breakpoint.    
      else if (!fEnable && m_state != BPS_DISABLED)    
      {    
         hr = m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);    
         if (hr == S_OK)    
         {    
            // Change the state of the breakpoint to BPS_DISABLED.    
            m_state = BPS_DISABLED;    
         }    
      }    
      else    
      {    
         hr = S_FALSE;    
      }    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)