---
title: "BP_UNBOUND_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "Énumération de BP_UNBOUND_REASON"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

donne la raison qu'un point d'arrêt a été annulé la liaison.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## Membres  
 BPUR\_UNKNOWN  
 la raison est inconnue.  
  
 BPUR\_CODE\_UNLOADED  
 Code contenant le point d'arrêt a été déchargé.  
  
 BPUR\_BREAKPOINT\_REBIND  
 Le point d'arrêt a été relié à nouveau à un emplacement différent.  Cela peut se produire après modification et continue des opérations lorsque le point d'arrêt est déplacé, ou lorsque le point d'arrêt est lié à un fichier avec un chemin d'accès qui n'est plus valide.  
  
 BPUR\_ BREAKPOINT\_ERROR  
 Le point d'arrêt est déterminé pour être dans l'erreur après avoir été lié.  Cela arrive à des points d'arrêt managés dans les conditions ne sont plus valides.  
  
## Notes  
 retourné par la méthode d' [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)