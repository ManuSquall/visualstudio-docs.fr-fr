---
title: "IDebugPropertyDestroyEvent2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyDestroyEvent2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugPropertyDestroyEvent2::GetDebugProperty"
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPropertyDestroyEvent2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la propriété soit détruit.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Paramètres  
 `ppProperty`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la propriété à détruire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)