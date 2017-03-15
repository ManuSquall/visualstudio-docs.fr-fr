---
title: "IDebugDisassemblyStream2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetSize"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetSize"
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la taille dans l'instruction de ce flux du code machine.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```c#  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### Paramètres  
 `pnSize`  
 \[out\]  Retourne la taille, dans l'instruction.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La valeur retournée par cette méthode peut être utilisée pour allouer un tableau de structures de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) qui est ensuite passé à la méthode d' [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
## Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)