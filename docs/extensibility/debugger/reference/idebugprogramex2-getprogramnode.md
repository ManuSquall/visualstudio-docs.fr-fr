---
title: "IDebugProgramEx2::GetProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEx2::GetProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nœud de programmation associé à un programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetProgramNode(   
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProgramNode(   
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### Paramètres  
 `ppProgramNode`  
 \[out\]  Retourne un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le nœud de programmation associé à ce programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)