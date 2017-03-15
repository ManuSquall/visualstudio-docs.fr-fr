---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne un objet de contexte de code correspondant à un identificateur spécifié d'emplacement du code.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Paramètres  
 `uCodeLocationId`  
 \[in\]  Spécifie l'identificateur de l'emplacement du code.  Consultez la section Notes de la méthode d' [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) pour une description d'un identificateur d'emplacement du code.  
  
 `ppCodeContext`  
 \[out\]  Retourne un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente le contexte de code associé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'identificateur de l'emplacement du code peut être retourné par un appel à la méthode d' [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) et peuvent apparaître dans la structure de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Pour convertir un contexte de code dans un identificateur de l'emplacement du code, appelez la méthode d' [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) .  
  
## Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)