---
title: "BP_LOCATION_RESOLUTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_RESOLUTION"
helpviewer_keywords: 
  - "Structure BP_LOCATION_RESOLUTION"
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# BP_LOCATION_RESOLUTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit la résolution d'un point d'arrêt à un emplacement spécifique.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## Membres  
 pResolution  
 l'objet d' [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) qui détermine le type du point d'arrêt et de ses informations sur la résolution.  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)