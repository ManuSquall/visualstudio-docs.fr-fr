---
title: "IEnumDebugObjects::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Next"
helpviewer_keywords: 
  - "IEnumDebugObjects::Next (méthode)"
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugObjects::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne l'ensemble suivant d'éléments de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Tableau d'éléments d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)