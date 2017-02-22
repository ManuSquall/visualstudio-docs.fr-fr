---
title: "BP_PASSCOUNT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT"
helpviewer_keywords: 
  - "Structure BP_PASSCOUNT"
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit le nombre et les conditions sur lesquels un point d'arrêt conditionnel est déclenché.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```c#  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## Membres  
 `dwPassCount`  
 Le nombre de fois de consulter le point d'arrêt avant de se déclencher.  
  
 `stylePassCount`  
 une valeur de l'énumération de [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) qui spécifie le style du nombre de passage de point d'arrêt.  
  
## Notes  
 cette structure est un membre de la structure de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .  
  
 Cette structure est également passé comme paramètre aux méthodes de[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) et de[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)