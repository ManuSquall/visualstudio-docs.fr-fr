---
title: "IDebugProgram2::GetProgramId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProgramId"
helpviewer_keywords: 
  - "IDebugProgram2::GetProgramId"
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient un GUID pour ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### Paramètres  
 `pguidProgramId`  
 \[out\]  Retourne `GUID` pour ce programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un moteur \(DE\) de débogage doit retourner l'identificateur de programme initialement passé aux méthodes d' [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  Cela permet l'ID du programme entre les composants du débogueur.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)