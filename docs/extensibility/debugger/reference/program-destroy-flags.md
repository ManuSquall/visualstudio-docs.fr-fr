---
title: "PROGRAM_DESTROY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Énumération de PROGRAM_DESTROY_FLAGS"
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PROGRAM_DESTROY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Énumère les valeurs correctes du programme détruisent des balises.  
  
## Syntaxe  
  
```cpp#  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```c#  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## termes  
 PROGRAM\_DESTROY\_CONTINUE\_DEBUGGING  
 Supprimez le programme, mais continuez à déboguer.  
  
## Notes  
 l'énumération est retournée par la méthode d' [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) .  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)