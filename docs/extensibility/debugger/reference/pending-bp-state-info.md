---
title: "PENDING_BP_STATE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PENDING_BP_STATE_INFO"
helpviewer_keywords: 
  - "Structure PENDING_BP_STATE_INFO"
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient des informations sur l'état d'un point d'arrêt qui est prêt à le lier à un emplacement du code.  
  
## Syntaxe  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```c#  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## Membres  
 État  
 une valeur de l'énumération de [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) qui spécifie l'état du point d'arrêt en attente.  
  
 balises  
 Une combinaison des indicateurs d'énumération de [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) qui spécifie si le point d'arrêt est en mode virtualisé.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md) où elle est terminée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)   
 [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)