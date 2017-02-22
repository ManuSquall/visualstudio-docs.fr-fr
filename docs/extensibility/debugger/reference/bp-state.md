---
title: "BP_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_STATE"
helpviewer_keywords: 
  - "Énumération de BP_STATE"
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie l'existence d'un point d'arrêt lié et spécifie également s'il est activé.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```c#  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## Membres  
 BPS\_NONE  
 spécifie qu'aucun point d'arrêt n'existe.  
  
 BPS\_DELETED  
 spécifie que le point d'arrêt a été supprimé.  
  
 BPS\_DISABLED  
 spécifie que le point d'arrêt est désactivé.  
  
 BPS\_ENABLED  
 spécifie que le point d'arrêt est activé.  
  
## Notes  
 Retourné par la méthode d' [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)