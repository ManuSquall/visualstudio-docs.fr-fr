---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElements (méthode)"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient un énumérateur de tous les éléments du tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) qui permet d'énumérer sein de tous les éléments.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Sinon, utilisez les méthodes d' [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) et d' [GetElement](../Topic/IDebugArrayObject::GetElement.md) pour itérer au sein de les éléments.  
  
## Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)