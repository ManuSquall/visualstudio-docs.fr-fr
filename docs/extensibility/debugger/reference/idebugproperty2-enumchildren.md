---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une liste des enfants de la propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) qui spécifie quels champs dans les structures énumérées de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) doivent être effectués.  
  
 `dwRadix`  
 \[in\]  Spécifie la base à utiliser lors de la mise en forme toutes les informations numériques.  
  
 `guidFilter`  
 \[in\]  GUID du filtre utilisé avec les paramètres d' `dwAttribFilter` et d' `pszNameFilter` pour sélectionner que des enfants d' `DEBUG_PROPERTY_INFO` doivent être énuméré.  Par exemple, filtres d' `guidFilterLocals` pour les variables locales.  
  
 `dwAttribFilter`  
 \[in\]  Une combinaison des indicateurs d'énumération de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) qui spécifie le type d'objets à énumérer, par exemple `DBG_ATTRIB_METHOD` de toutes les méthodes qui peuvent être des enfants de cette propriété.  Utilisé conjointement avec les paramètres d' `guidFilter` et d' `pszNameFilter` .  
  
 `pszNameFilter`  
 \[in\]  le nom du filtre utilisé avec les paramètres d' `guidFilter` et d' `dwAttribFilter` pour sélectionner que des enfants d' `DEBUG_PROPERTY_INFO` doivent être énuméré.  Par exemple, affecter à ce paramètre en « MyX » filtre tous les enfants avec le nom « MyX ».  
  
 `dwTimeout`  
 \[in\]  Spécifie le temps maximum, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenant une liste des propriétés enfants.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)