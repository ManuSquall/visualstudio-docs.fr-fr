---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit une référence.  Réservé à une utilisation future.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) qui déterminent les champs à terminer la structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 `nRadix`  
 \[in\]  La base à utiliser lors de la mise en forme toute information numériques.  
  
 `dwTimeout`  
 \[in\]  Durée maximale, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
 `rgpArgs`  
 \[in\]  Un tableau d'objets d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  Réservé à une utilisation ultérieure ; ensemble à une valeur NULL.  
  
 `dwArgCount`  
 \[in\]  Le nombre d'arguments de référence dans le tableau d' `rgpArgs` .  Réservé à une utilisation ultérieure ; affectez à la valeur 0.  
  
 `pReferenceInfo`  
 \[out\]  Une structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui est terminée avec une description de la propriété.  
  
## Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)