---
title: "IEnumDebugProcesses2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugProcesses2::Next"
helpviewer_keywords: 
  - "IEnumDebugProcesses2::Next"
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugProcesses2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne l'ensemble suivant d'éléments de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProcess2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint             celt,  
   IDebugProcess2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Tableau d'éléments d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)