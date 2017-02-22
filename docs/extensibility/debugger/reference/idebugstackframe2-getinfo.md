---
title: "IDebugStackFrame2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetInfo"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetInfo"
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient une description du frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```c#  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### Paramètres  
 `dwFieldSpec`  
 \[in\]  Une combinaison des indicateurs d'énumération de [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie les champs du paramètre d' `pFrameInfo` doivent être effectués.  
  
 `nRadix`  
 \[in\]  La base à utiliser lors de la mise en forme toute information numériques.  
  
 `pFrameInfo`  
 \[out\]  Une structure de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) qui est terminée avec la description du frame de pile.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)