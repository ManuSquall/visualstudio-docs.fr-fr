---
title: "IDebugSymbolProvider::GetContextFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetContextFromAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetContextFromAddress (méthode)"
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetContextFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode mappe une adresse de débogage dans un contexte de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetContextFromAddress(   
   IDebugAddress*           pAddress,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetContextFromAddress(  
   IDebugAddress              pAddress,   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  l'adresse de débogage comme représentée par une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `ppDocContext`  
 \[out\]  Retourne un contexte de document comme représenté par une interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)