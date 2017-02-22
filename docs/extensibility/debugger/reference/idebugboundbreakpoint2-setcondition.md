---
title: "IDebugBoundBreakpoint2::SetCondition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition (méthode)"
  - "IDebugBoundBreakpoint2::SetCondition (méthode)"
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit ou modifie la condition associée à ce point d'arrêt lié.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### Paramètres  
 `bpCondition`  
 \[in\]  une valeur de l'énumération de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui décrit la condition.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si l'état de l'objet de point d'arrêt lié est défini à `BPS_DELETED` \(une partie de l'énumération de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Notes  
 Toute condition qui a été précédemment associée à ce point d'arrêt est perdue.  
  
## Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)