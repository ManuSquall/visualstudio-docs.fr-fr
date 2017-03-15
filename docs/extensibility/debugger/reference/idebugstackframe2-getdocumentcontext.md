---
title: "IDebugStackFrame2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le contexte de le document pour ce frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### Paramètres  
 `ppCxt`  
 \[out\]  Retourne un objet d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représente la position actuelle dans un document source.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est plus rapide que appelant la méthode d' [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) puis appelant la méthode d' [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) sur le contexte de code.  Toutefois, il n'est pas garanti que chaque moteur \(DE\) de débogage appliquera cette méthode.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)