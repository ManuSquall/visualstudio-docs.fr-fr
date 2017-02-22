---
title: "ATTACH_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATTACH_REASON"
helpviewer_keywords: 
  - "Énumération de ATTACH_REASON"
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# ATTACH_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie la raison pour que le moteur de \(DE\) débogage se s'attache à un nœud de programme.  
  
## Syntaxe  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## Membres  
 ATTACH\_REASON\_AUTO  
 Attachez car le processus est actuellement en mode débogage.  
  
 ATTACH\_REASON\_LAUNCH  
 Attachez parce que le processus a été lancé.  
  
 ATTACH\_REASON\_USER  
 Attachement à cause d'une demande de l'utilisateur.  
  
## Notes  
 ces valeurs sont utilisées comme paramètre aux méthodes d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) et d' [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)