---
title: "IEnumDebugModules2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Next"
helpviewer_keywords: 
  - "IEnumDebugModules2::Next"
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugModules2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne l'ensemble suivant d'éléments de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Tableau d'éléments d' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)