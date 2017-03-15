---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "Énumération de PROCESS_INFO_FLAGS"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit ou spécifie les propriétés d'un processus.  
  
## Syntaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Membres  
 PIFLAG\_SYSTEM\_PROCESS  
 indique que le processus est un processus système.  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 indique que le processus est débogué par un débogueur.  Ce peut être un débogueur de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , ou peut être un autre débogueur, par exemple, WinDbg.  
  
 PIFLAG\_PROCESS\_STOPPED  
 Indique le processus est arrêté.  Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié.  Disponible dans [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] et versions ultérieures.  
  
 PIFLAG\_PROCESS\_RUNNING  
 Indique le processus s'exécute.  Valide uniquement si `PIFLAG_DEBUGGER_ATTACHED` est également spécifié.  Disponible dans [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] et versions ultérieures.  
  
## Notes  
 utilisé pour le membre d' `Flags` de la structure de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)