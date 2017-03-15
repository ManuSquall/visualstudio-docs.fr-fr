---
title: "IEnumDebugCustomAttributes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Next"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Next"
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait un nombre spécifié d'attributs personnalisés dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à récupérer.  Spécifie également la taille maximale du tableau d' `rgelt` .  
  
 `rgelt`  
 \[out\]  Un tableau d'objets d' [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Retourne le nombre d'éléments réellement retournés dans `rgelt`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si inférieur au nombre demandé d'éléments peuvent être retournés ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)