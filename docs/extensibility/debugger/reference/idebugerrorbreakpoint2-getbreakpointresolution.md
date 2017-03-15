---
title: "IDebugErrorBreakpoint2::GetBreakpointResolution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpoint2::GetBreakpointResolution"
helpviewer_keywords: 
  - "IDebugErrorBreakpoint2::GetBreakpointResolution"
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugErrorBreakpoint2::GetBreakpointResolution
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la résolution d'erreur de point d'arrêt qui décrit l'erreur.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetBreakpointResolution(   
   IDebugErrorBreakpointResolution2** ppErrorResolution  
);  
```  
  
```c#  
int GetBreakpointResolution(   
   out IDebugErrorBreakpointResolution2 ppErrorResolution  
);  
```  
  
#### Paramètres  
 `ppErrorResolution`  
 \[out\]  Retourne un objet d' [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) qui décrit l'erreur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)