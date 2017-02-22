---
title: "IDebugPortNotify2::RemoveProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Annule l'inscription d'un programme qui peut être mis au point du port qu'il s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Paramètres  
 `pProgramNode`  
 \[in\]  Un objecy d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le programme d'annuler l'enregistrement.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode supprime un nœud de programme qui a été ajouté à un appel à la méthode d' [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) .  
  
## Voir aussi  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)