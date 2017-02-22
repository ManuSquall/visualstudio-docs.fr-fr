---
title: "IDebugPendingBreakpoint2::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Bind"
helpviewer_keywords: 
  - "Bind (méthode)"
  - "IDebugPendingBreakpoint2::Bind (méthode)"
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lie ce point d'arrêt en attente à un ou plusieurs emplacements de code.  
  
## Syntaxe  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```c#  
int Bind();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si le point d'arrêt a été supprimé.  
  
## Notes  
 Lorsque cette méthode est appelée, un moteur de \(DE\) débogage doit essayer de lier ce point d'arrêt en attente à tous les emplacements de code qui correspondent.  
  
 Une fois que cette méthode retourne, l'appelant doit attendre des événements qui indique que le point d'arrêt en attente est lié ou est dans l'erreur avant à condition que les appels à [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) ou l' [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).methods énumèreront tous les points d'arrêt limitent d'erreur ou, respectivement.  
  
## Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)