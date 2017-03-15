---
title: "IEnumDebugReferenceInfo2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Next"
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugReferenceInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne l'ensemble suivant d'éléments de l'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG                   celt,  
   DEBUG_REFERENCE_INFO ** rgelt,  
   ULONG*                  pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                   celt,  
   DEBUG_REFERENCE_INFO[] rgelt,  
   ref uint               pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Tableau des éléments de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)