---
title: "IDebugPendingBreakpoint2::Enable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Enable"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::Enable (méthode)"
  - "Enable (méthode)"
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Enable
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

bascule l'état actif du point d'arrêt en attente.  
  
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
 \[in\]  Affectez une valeur différente de zéro \(`TRUE`\) pour permettre à un point d'arrêt en attente, ou à zéro \(`FALSE`\) pour désactiver.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si le point d'arrêt a été supprimé.  
  
## Notes  
 Lorsqu'un point d'arrêt en attente est activé ou désactivé, tous les points d'arrêt liés de lui sont définis au même état.  
  
 Appeler cette méthode autant de fois que nécessaire, même si le point d'arrêt est déjà activé ou désactivé.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CPendingBreakpoint` qui expose l'interface d' [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
```cpp#  
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the bound breakpoint member variable is valid, then enable or   
      // disable the bound breakpoint.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Enable(fEnable);    
      }    
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to enabled or disabled depending on the passed BOOL condition.    
      m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;    
      hr = S_OK;    
  
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)