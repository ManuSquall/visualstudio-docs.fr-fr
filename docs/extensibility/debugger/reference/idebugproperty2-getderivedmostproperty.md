---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la propriété dérivée\-plus d'une propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### Paramètres  
 `ppDerivedMost`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la propriété dérivée\-plus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `S_GETDERIVEDMOST_NO_DERIVED_MOST` s'il n'y a aucune propriété dérivée\-plus à récupérer.  
  
## Notes  
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` mais qui est une instanciation d' `ClassDerived` qui est dérivée d' `ClassRoot`, puis cette méthode retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) décrivant l'objet d' `ClassDerived` .  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)