---
title: "IDebugBreakpointEvent2::EnumBreakpoints | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBreakpointEvent2::EnumBreakpoints
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur pour tous les points d'arrêt qui les a déclenché à l'emplacement actuel du code.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumBreakpoints(  
  IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```c#  
int EnumBreakpoints(  
  out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) qui énumère tous les points d'arrêt associés à l'emplacement actuel du code.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Tous les points d'arrêt à un emplacement particulier peut se déclencher à un moment particulier \(par exemple, un point d'arrêt dans une condition ne le déclenche pas tant que cette condition est remplie.\)  
  
## Voir aussi  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)