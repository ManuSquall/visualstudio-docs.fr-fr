---
title: "MODULE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "Énumération de MODULE_FLAGS"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

utilisé pour décrire un module.  
  
## Syntaxe  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Membres  
 MODULE\_FLAG\_NONE  
 ne spécifie aucun module.  
  
 MODULE\_FLAG\_SYSTEM  
 Spécifie un module du système.  
  
 MODULE\_FLAG\_SYMBOLS  
 spécifie un module de symbole.  
  
 MODULE\_FLAG\_64BIT  
 spécifie un module 64 bits.  
  
 MODULE\_FLAG\_OPTIMIZED  
 spécifie le module a été optimisé.  Cet état est répercutée dans la fenêtre de **Module** .  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 spécifie le module n'a pas été optimisé.  Cet état est répercutée dans la fenêtre de **Module** .  C'est la condition par défaut.  
  
## Notes  
 utilisé pour le membre d' `m_dwModuleFlags` de la structure de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)