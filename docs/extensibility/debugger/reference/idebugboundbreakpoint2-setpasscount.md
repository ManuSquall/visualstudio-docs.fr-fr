---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount (méthode)"
  - "IDebugBoundBreakpoint2::SetPassCount (méthode)"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit ou modifie le nombre de passage associé à ce point d'arrêt lié.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Paramètres  
 `bpPassCount`  
 \[in\]  la structure de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui spécifie le nombre de passage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si l'état de l'objet de point d'arrêt lié est défini à `BPS_DELETED` \(une partie de l'énumération de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Notes  
 Le nombre de exécution détermine lorsque le point d'arrêt est déclenché.  La série ou le nombre d'accès actuel peut être obtenu en appelant la méthode d' [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) .  
  
 Tout nombre de tests qui a été précédemment associé à ce point d'arrêt est perdu.  
  
## Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)