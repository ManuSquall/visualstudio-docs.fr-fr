---
title: "CONST_GUID_ARRAY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONST_GUID_ARRAY"
helpviewer_keywords: 
  - "Structure CONST_GUID_ARRAY"
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Une structure contenant une liste d' `GUID`S.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```c#  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## Membres  
 dwCount  
 Nombre d' `GUID`s dans le tableau d' `Members` .  
  
 Membres  
 Tableau d' `GUID`S.  
  
## Notes  
 Cette structure est passée à la méthode d' [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) , et est retourné des méthodes d' [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) et d' [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) .  
  
 Le propriétaire d'une instance de cette structure est chargé de libérer de la mémoire alloué.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)