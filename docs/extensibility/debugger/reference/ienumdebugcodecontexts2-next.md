---
title: "IEnumDebugCodeContexts2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2::Next"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Next"
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCodeContexts2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne l'ensemble suivant d'éléments de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext2** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                 celt,  
   IDebugCodeContext2[] rgelt,  
   ref uint             pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Tableau d'éléments d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)