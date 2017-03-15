---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une liste des frames de pile pour ce thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### Paramètres  
 `dwFieldSpec`  
 \[in\]  Une combinaison des indicateurs d'énumération de [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie les champs des structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) doivent être effectués.  Spécifiez la balise d' `FIF_FUNCNAME_FORMAT` formater le nom de fonction dans une seule chaîne.  
  
 `nRadix`  
 \[in\]  Base utilisée pour la mise en forme des informations numériques dans l'énumérateur.  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) qui contient une liste de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) décrivant le frame de pile.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les trames de threads sont énumérés dans l'ordre, avec le frame actuel énuméré en premier et le frame le plus ancien énuméré en dernier.  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)