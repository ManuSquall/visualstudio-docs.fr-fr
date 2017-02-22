---
title: "EXCEPTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "Structure EXCEPTION_INFO"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit une exception ou une erreur d'exécution levée par le programme débogué.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## Membres  
 pProgram  
 L'objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme où l'exception s'est produite.  
  
 bstrProgramName  
 Le nom du programme où l'exception s'est produite.  
  
 bstrExceptionName  
 Nom de l'exception.  
  
 dwCode  
 Code d'identification de l'exception ou erreur d'exécution.  
  
 dwState  
 une valeur de l'énumération d' [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) qui définit l'état de l'exception.  
  
 guidType  
 L'identificateur de langue du GUID, `guidLang` ou `guidEng`.  
  
## Notes  
 Cette structure est passée à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) et aux méthodes d' [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .  Cette structure est également passé à la méthode d' [GetException](../Topic/IDebugExceptionEvent2::GetException.md) à accomplir.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../Topic/IDebugExceptionEvent2::GetException.md)