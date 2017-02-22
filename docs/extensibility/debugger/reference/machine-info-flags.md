---
title: "MACHINE_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO_FLAGS"
helpviewer_keywords: 
  - "Énumération de MACHINE_INFO_FLAGS"
ms.assetid: 1482095d-9a2e-4ef1-9e14-362c0b85194e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MACHINE_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

utilisé pour décrire un ordinateur.  
  
## Syntaxe  
  
```cpp#  
enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
typedef DWORD MACHINE_INFO_FLAGS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
```  
  
## Membres  
 MCIFLAG\_TERMINAL\_SERVICES\_AVAILABLE  
 indique que les services terminaux sont disponibles.  
  
## Notes  
 Utilisé comme membre d' `Flags` de la structure de [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)