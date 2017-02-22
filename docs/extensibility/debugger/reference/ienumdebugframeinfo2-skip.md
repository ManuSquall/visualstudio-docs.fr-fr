---
title: "IEnumDebugFrameInfo2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2::Skip"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2::Skip"
ms.assetid: 68cd3948-022a-41ad-bd9f-9ab776cf6248
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugFrameInfo2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sauts sur le nombre spécifié d'éléments.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si `celt` est supérieur au nombre d'éléments restants ; sinon, retourne un code d'erreur.  
  
## Notes  
 Si `celt` spécifie une valeur supérieure au nombre d'éléments restants, l'énumération est définie à la fin et `S_FALSE` est retourné.  
  
## Voir aussi  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)