---
title: "IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetHitCount"
helpviewer_keywords: 
  - "GetHitCount (méthode)"
  - "IDebugBoundBreakpoint2::GetHitCount (méthode)"
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nombre d'accès actuel pour cela lie le point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```c#  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### Paramètres  
 `pdwHitCount`  
 \[out\]  Retourne le nombre d'accès.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_BP_DELETED` si l'état de l'objet de point d'arrêt lié est défini à `BPS_DELETED` \(une partie de l'énumération de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Notes  
 Il est le nombre de fois où ce point d'arrêt un déclenchés pendant la série de tests actuelle de session.  
  
## Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)