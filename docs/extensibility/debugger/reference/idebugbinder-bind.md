---
title: "IDebugBinder::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::Bind"
helpviewer_keywords: 
  - "IDebugBinder::Bind (méthode)"
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le contexte ou l'objet de mémoire qui contiennent la valeur actuelle du symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `pContainer`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui contient l'enfant a référencé par `pField`.  
  
 `pField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le symbole.  
  
 `ppObject`  
 \[out\]  Retourne `IDebugObject` qui représente l'instance du symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)