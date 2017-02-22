---
title: "BP_LOCATION_CODE_CONTEXT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_CONTEXT"
helpviewer_keywords: 
  - "Structure BP_LOCATION_CODE_CONTEXT"
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_CONTEXT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit l'emplacement d'un point d'arrêt qui est lié directement à une adresse dans le programme débogué.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## Membres  
 pCodeContext  
 L'objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui identifie la position du point d'arrêt dans le code.  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)