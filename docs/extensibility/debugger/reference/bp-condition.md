---
title: "BP_CONDITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_CONDITION"
helpviewer_keywords: 
  - "Structure BP_CONDITION"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit les conditions dans lesquelles un point d'arrêt se déclenche.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Membres  
 `pThread`  
 L'objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread actif de l'application qui contient le point d'arrêt.  
  
 `styleCondition`  
 une valeur de l'énumération de [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) décrivant le style de cette condition de point d'arrêt.  
  
 `bstrContext`  
 l'emplacement du point d'arrêt.  
  
 `bstrCondition`  
 La condition de mise à déclencher du point d'arrêt.  
  
 `nRadix`  
 Base à utiliser lors de l'évaluation des informations numériques.  
  
## Notes  
 cette structure est un membre des structures de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 Cette structure est également passé comme paramètre aux méthodes d' [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) et d' [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)