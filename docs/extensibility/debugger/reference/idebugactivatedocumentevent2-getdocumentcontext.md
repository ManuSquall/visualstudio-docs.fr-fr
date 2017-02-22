---
title: "IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "GetDocumentContext (méthode)"
  - "IDebugActivateDocumentEvent2::GetDocumentContext (méthode)"
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugActivateDocumentEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le contexte de document qui décrit la position dans le document qui doit être rendu actif par le package de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Paramètres  
 `ppDocContext`  
 \[out\]  Retourne un objet d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représente une position dans un document du fichier source.  
  
## Notes  
 Cette position peut être utilisée pour afficher le signe insertion, par exemple.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)