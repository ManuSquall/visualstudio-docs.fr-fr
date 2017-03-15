---
title: "IDebugPortEx2::GetProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::GetProgram"
helpviewer_keywords: 
  - "IDebugPortEx2::GetProgram"
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::GetProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le programme associé à un nœud de programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```c#  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### Paramètres  
 `pProgramNode`  
 \[in\]  Un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) représentant le nœud de programme.  
  
 `ppProgram`  
 \[out\]  Retourne un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme associé au nœud de programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)