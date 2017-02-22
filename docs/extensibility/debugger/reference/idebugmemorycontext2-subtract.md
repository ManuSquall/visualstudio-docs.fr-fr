---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Soustraction (méthode)"
  - "IDebugMemoryContext2::Subtract (méthode)"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Soustrait la valeur spécifiée du contexte actuel et retourne un nouveau contexte.  
  
## Syntaxe  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Paramètres  
 `dwCount`  
 \[in\]  le nombre d'octets de mémoire à décrémenter.  
  
 `ppMemCxt`  
 \[out\]  Retourne un nouvel objet d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un contexte de mémoire est une adresse, donc soustrayant une valeur d'une adresse produit une nouvelle adresse qui requiert une nouvelle interface de contexte.  
  
 Cette méthode doit toujours produire un nouveau contexte, même si l'adresse résultant est en dehors de l'espace mémoire associé à ce contexte.  La seule exception est si aucune mémoire ne peut être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur NULL \(qui est une erreur\).  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)