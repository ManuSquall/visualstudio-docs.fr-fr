---
title: "IDebugProcess2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetServer"
helpviewer_keywords: 
  - "IDebugProcess2::GetServer"
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProcess2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le serveur que ce processus s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```c#  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### Paramètres  
 `ppServer`  
 \[out\]  Retourne un objet d' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui représente le serveur sur lequel ce processus s'exécute.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Plusieurs serveurs peut s'exécuter sur un ordinateur unique.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)