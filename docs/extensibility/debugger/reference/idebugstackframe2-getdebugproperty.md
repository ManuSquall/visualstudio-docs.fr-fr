---
title: "IDebugStackFrame2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDebugProperty"
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient une description des propriétés d'un frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```c#  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### Paramètres  
 `ppDebugProp`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui décrit les propriétés de ce frame de pile.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Appeler la méthode d' [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) avec les filtres appropriés peut récupérer les variables locales, des paramètres de méthode, des registres, et le pointeur « this » associé au frame de pile.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)