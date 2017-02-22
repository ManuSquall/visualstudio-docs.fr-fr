---
title: "IDebugProcess2::GetProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetProcessId"
helpviewer_keywords: 
  - "IDebugProcess2::GetProcessId"
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le GUID de ce processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```c#  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### Paramètres  
 `pguidProcessId`  
 \[out\]  Retourne le GUID de ce processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'identificateur global unique identifie ce processus de tous les autres processus qui s'exécutent dans le système.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)