---
title: "IEnumDebugObjects::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Skip"
helpviewer_keywords: 
  - "IEnumDebugObjects::Skip (méthode)"
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode rejette sur le nombre spécifié d'éléments.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```c#  
int Skip(  
   [In] uint celt  
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)