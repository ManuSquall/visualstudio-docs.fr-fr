---
title: "IDebugBinder::ResolveDynamicType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveDynamicType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveDynamicType (méthode)"
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBinder::ResolveDynamicType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne le type exact d'une variable.  
  
## Syntaxe  
  
```cpp#  
HRESULT ResolveDynamicType (  
   IDebugDynamicField *pDynamic,  
   IDebugField       **ppResolved  
);  
```  
  
```c#  
int ResolveDynamicType(  
   IDebugDynamicField pDynamic,   
   out IDebugField    ppResolved  
);  
```  
  
#### Paramètres  
 `pDynamic`  
 \[in\]  [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) représentant un type d'une variable.  
  
 `ppResolved`  
 \[out\]  Retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui donnent des informations spécifiques sur le type de la variable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)