---
title: "IDebugMemoryBytes2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::GetSize"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::GetSize (méthode)"
  - "GetSize (méthode)"
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère la taille, en octets, de la mémoire représentée par cet objet d' [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) .  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```c#  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### Paramètres  
 `pqwSize`  
 \[out\]  Retourne la taille, en octets de l'espace mémoire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)