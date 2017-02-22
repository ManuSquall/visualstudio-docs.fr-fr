---
title: "IDebugObject::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugObject::GetMemoryContext (méthode)"
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le contexte de mémoire qui représente l'adresse de la valeur de l'objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```c#  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### Paramètres  
 `pContext`  
 \[out\]  Retourne un objet d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) représentant l'adresse de la valeur de l'objet.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 le contexte retourné de mémoire spécifie l'adresse de la valeur comme représentée par cet objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)