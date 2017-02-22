---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Add (méthode)"
  - "Add (méthode)"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ajoute la valeur spécifiée au contexte actuel et retourne un nouveau contexte.  
  
## Syntaxe  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Paramètres  
 `dwCount`  
 \[in\]  la valeur à ajouter au contexte actuel.  
  
 `ppMemCxt`  
 \[out\]  Retourne un nouvel objet d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un contexte de mémoire est une adresse, donc ajoutant une valeur à une adresse produit une nouvelle adresse qui requiert une nouvelle interface de contexte.  
  
 Cette méthode doit toujours produire un nouveau contexte, même si l'adresse résultant est en dehors de l'espace mémoire associé à ce contexte.  La seule exception est si aucune mémoire ne peut être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur NULL \(qui est une erreur\).  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)