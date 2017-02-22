---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

S'attache au programme associé ou diffère le processus d'attachement à la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## Syntaxe  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### Paramètres  
 `guidProgramId`  
 \[in\]  `GUID` à assigner au programme associé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée pendant le processus d'attachement, avant que la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) soit appelée.  La méthode d' `OnAttach` peut exécuter le processus d'attachement lui\-même \(dans ce cas, cette méthode retourne `S_FALSE`\) ou différer le processus d'attachement à la méthode d' `IDebugEngine2::Attach` \(méthode d' `OnAttach` retourne `S_OK`\).  Dans l'un ou l'autre événement, la méthode d' `OnAttach` peut définir `GUID` du programme débogué à `GUID`donné.  
  
## Voir aussi  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)