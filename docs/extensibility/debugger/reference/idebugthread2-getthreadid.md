---
title: "IDebugThread2::GetThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetThreadId"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadId"
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient l'ID de thread système.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```c#  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### Paramètres  
 `pdwThreadId`  
 \[out\]  Retourne l'ID de thread système.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un ID de thread est utilisé pour identifier un thread entre tous les autres threads d'un processus.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CProgram` qui implémente l'interface d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)