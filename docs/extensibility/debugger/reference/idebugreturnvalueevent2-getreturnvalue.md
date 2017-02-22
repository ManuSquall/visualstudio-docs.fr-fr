---
title: "IDebugReturnValueEvent2::GetReturnValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReturnValueEvent2::GetReturnValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la valeur retournée sur sortir pas \- ou sur une fonction.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetReturnValue (   
   IDebugProperty2** ppReturnValue  
);  
```  
  
```c#  
int GetReturnValue (   
   out IDebugProperty2 ppReturnValue  
);  
```  
  
#### Paramètres  
 `ppReturnValue`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la valeur à récupérer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)