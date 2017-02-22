---
title: "IDebugPointerField::GetDereferencedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField::GetDereferencedField"
helpviewer_keywords: 
  - "IDebugPointerField::GetDereferencedField (méthode)"
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne le type d'objet auquel les points de cet objet de pointeur.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### Paramètres  
 `ppField`  
 \[out\]  Retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le type d'objet cible.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Si, par exemple, les points d'objet d' [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) en entier, le type d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) retourné par cette méthode décrit qu'entier tapez.  
  
## Voir aussi  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)