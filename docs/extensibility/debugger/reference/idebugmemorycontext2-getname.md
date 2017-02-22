---
title: "IDebugMemoryContext2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetName"
helpviewer_keywords: 
  - "IDebugMemoryContext2::GetName (méthode)"
  - "GetName (méthode)"
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait le nom utilisateur\-affichable dans ce contexte.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(  
   out string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Retourne le nom du contexte de mémoire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le nom d'un contexte de mémoire n'est pas utilisé normalement.  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)