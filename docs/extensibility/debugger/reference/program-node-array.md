---
title: "PROGRAM_NODE_ARRAY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROGRAM_NODE_ARRAY"
helpviewer_keywords: 
  - "Structure PROGRAM_NODE_ARRAY"
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROGRAM_NODE_ARRAY
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient un tableau d'objets qui décrivent les programmes d'intérêt.  
  
## Syntaxe  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```c#  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## Membres  
 dwCount  
 Nombre d'objets dans le tableau d' `Members` .  
  
 Membres  
 Un tableau d'objets d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) décrivant les programmes demandés.  
  
## Notes  
 Cette structure fait partie de la structure de [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) qui est ensuite effectuée par un appel à la méthode d' [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)