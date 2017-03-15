---
title: "IDebugBinder3::GetMemoryObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetMemoryObject"
helpviewer_keywords: 
  - "IDebugBinder3::GetMemoryObject (méthode)"
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetMemoryObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait un objet mémoire qui représente la mémoire que cet objet est lié.  
  
## Syntaxe  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `pField`  
 \[in\]  Spécifie que le champ afin d'obtenir l'objet mémoire.  
  
 `uConstant`  
 \[in\]  représente une adresse mémoire ou une valeur pour une valeur de constante.  
  
 `ppObject`  
 \[out\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant la mémoire que cet objet est lié.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)