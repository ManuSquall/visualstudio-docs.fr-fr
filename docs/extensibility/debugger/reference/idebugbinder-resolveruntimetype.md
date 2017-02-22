---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveRuntimeType (méthode)"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode détermine le type d'exécution d'un objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### Paramètres  
 `pObject`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) à résoudre.  
  
 `ppResolved`  
 \[out\]  Retourne le type de l'objet comme [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le type d'exécution d'un objet n'est pas toujours connu au moment de la compilation.  Par exemple, à l'aide de le polymorphisme, un argument peut être passé à une fonction comme sa classe de base, telle qu'une classe du bouton.  L'argument réel peut être une classe dérivée, telle qu'une classe de case d'option.  
  
## Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)