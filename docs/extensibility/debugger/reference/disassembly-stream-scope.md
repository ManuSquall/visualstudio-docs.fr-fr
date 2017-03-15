---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "Énumération de DISASSEMBLY_STREAM_SCOPE"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie la portée du flux de code machine.  
  
## Syntaxe  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Membres  
 DSS\_HUGE  
 Spécifie que désassemble le contexte de code génère plus de sortie qu'un client devriez généralement extraire dans un seul appel.  
  
 DSS\_FUNCTION  
 Indique que la fonction contenue par le contexte de code doit être désassemblée.  Spécifie que le flux de code machine représente une fonction, une fois retourné par la méthode d' [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) .  
  
 DSS\_MODULE  
 Une fois retourné par la méthode d' `IDebugDisassemblyStream2::GetScope` , spécifie que le flux de code machine représente un module.  
  
 DSS\_ALL  
 Spécifie le code machine pour l'espace d'adressage entier.  
  
## Notes  
 passé comme argument à la méthode d' [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) et retourné par la méthode d' [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) .  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)