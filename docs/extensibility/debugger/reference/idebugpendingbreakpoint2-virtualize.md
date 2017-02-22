---
title: "IDebugPendingBreakpoint2::Virtualize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Virtualize"
helpviewer_keywords: 
  - "Virtualiser (méthode)"
  - "IDebugPendingBreakpoint2::Virtualize (méthode)"
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bascule l'état virtualisé de ce point d'arrêt en attente.  Lorsqu'un point d'arrêt en attente est virtualisé, le moteur de débogage tente de se lier chaque fois que le nouveau code chargé dans le programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### Paramètres  
 `fVirtualize`  
 \[in\]  Affectez une valeur différente de zéro \(`TRUE`\) pour virtualiser le point d'arrêt en attente, ou à zéro \(`FALSE`\) pour désactiver la virtualisation.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si le point d'arrêt a été supprimé.  
  
## Notes  
 Un point d'arrêt virtualisé est lié code chaque fois que est chargé.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CPendingBreakpoint` qui expose l'interface d' [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
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