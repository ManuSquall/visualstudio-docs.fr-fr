---
title: "IDebugThread2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetName"
helpviewer_keywords: 
  - "IDebugThread2::GetName"
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom d'un thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Retourne le nom du thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 le nom extrait est toujours un nom qui peut être affiché et ce nom décrit le thread.  Le nom de thread peut être dérivé d'une architecture à l'exécution qui prend en charge les threads nommés, ou être un nom dérivé du moteur de débogage.  Par ailleurs, le nom du thread peut être défini par un appel à la méthode d' [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)