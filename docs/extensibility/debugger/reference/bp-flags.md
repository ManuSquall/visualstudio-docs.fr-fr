---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "Énumération de BP_FLAGS"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fournit des indicateurs facultatifs qui peuvent être utilisées pour spécifier des informations supplémentaires en définissant un point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Membres  
 BP\_FLAG\_NONE  
 Ne spécifie pas de balise de point d'arrêt.  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 Spécifie que le moteur de débogage \(DE\) doit mapper le point d'arrêt à l'aide de la position de document.  Cela ne s'applique qu'aux points d'arrêt définis dans des fichiers sources script\-orientés tels qu'Active Server \(ASP\) Pages.  
  
 \_STOP DE BP\_FLAG\_DO NOT  
 Spécifie que le point d'arrêt doit être traité par le moteur de débogage, mais que le moteur de débogage finalement ne doit pas arrêter là \(autrement dit, un objet événement d' [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ne doit pas être envoyé\).  Cette balise est conçue pour être utilisée essentiellement avec les points de trace.  
  
## Notes  
 utilisé pour le membre d' `dwFlags` des structures de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)