---
title: "IDebugBinder::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugBinder::GetMemoryContext (méthode)"
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode convertit un emplacement d'objet ou une adresse mémoire à un contexte de mémoire.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Paramètres  
 `pField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant l'objet de rechercher.  Si `NULL`, puis utilisent la `dwConstant` à la place.  
  
 `dwConstant`  
 \[in\]  une adresse mémoire constante, telle que 0x5000.  
  
 `ppMemCxt`  
 \[out\]  Retourne l'interface d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui représente l'adresse de l'objet, ou l'adresse en mémoire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)