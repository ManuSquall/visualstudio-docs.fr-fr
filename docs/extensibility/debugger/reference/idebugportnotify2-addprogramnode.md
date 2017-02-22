---
title: "IDebugPortNotify2::AddProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::AddProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::AddProgramNode"
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::AddProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enregistre un programme qui peut être débogué avec le port qu'il s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT AddProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int AddProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Paramètres  
 `pProgramNode`  
 \[in\]  un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le programme à enregistrer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un nœud du programme peut être annulé du port en appelant la méthode d' [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .  
  
## Voir aussi  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)