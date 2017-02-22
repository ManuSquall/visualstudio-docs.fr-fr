---
title: "IDebugThreadDestroyEvent2::GetExitCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThreadDestroyEvent2::GetExitCode"
helpviewer_keywords: 
  - "IDebugThreadDestroyEvent2::GetExitCode"
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThreadDestroyEvent2::GetExitCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le code de sortie d'un thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExitCode (   
   DWORD* pdwExit  
);  
```  
  
```c#  
int GetExitCode (   
   out uint pdwExit  
);  
```  
  
#### Paramètres  
 `pdwExit`  
 \[out\]  Retourne un code de sortie du thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)