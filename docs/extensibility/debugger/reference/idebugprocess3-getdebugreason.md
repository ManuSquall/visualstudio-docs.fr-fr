---
title: "IDebugProcess3::GetDebugReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetDebugReason"
helpviewer_keywords: 
  - "IDebugProcess3::GetDebugReason"
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::GetDebugReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne la raison pour laquelle le processus a été lancé pour le débogage.  
  
## Syntaxe  
  
```cpp  
HRESULT GetDebugReason(  
   DEBUG_REASON* pReason  
);  
```  
  
```c#  
int GetDebugReason(  
   out enum_DEBUG_REASON pReason  
);  
```  
  
#### Paramètres  
 `pReason`  
 \[out\]  Retourne une valeur de l'énumération de [DEBUG\_REASON](../../../extensibility/debugger/reference/debug-reason.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DEBUG\_REASON](../../../extensibility/debugger/reference/debug-reason.md)