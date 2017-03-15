---
title: "SEEK_START | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_START"
helpviewer_keywords: 
  - "Énumération de SEEK_START"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie la position à partir duquel commencer à rechercher dans un flux de code machine.  
  
## Syntaxe  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## Membres  
 SEEK\_START\_BEGIN  
 Démarre la recherche au début du document actif.  
  
 SEEK\_START\_END  
 Démarre la recherche à la fin du document actif.  
  
 SEEK\_START\_CURRENT  
 Démarre la recherche à la position actuelle du document actif.  
  
 SEEK\_START\_CODECONTEXT  
 Démarre la recherche au contexte de code particulier du document actif.  
  
 SEEK\_START\_CODELOCID  
 Démarre la recherche à l'identificateur d'emplacement du code.  Des identificateurs d'emplacement du code sont obtenus en appelant [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md).  
  
## Notes  
 passé comme argument à la méthode d' [Recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)