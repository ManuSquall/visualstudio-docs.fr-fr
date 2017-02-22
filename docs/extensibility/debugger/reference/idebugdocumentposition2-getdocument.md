---
title: "IDebugDocumentPosition2::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetDocument"
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le document contenant.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```c#  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### Paramètres  
 `ppDoc`  
 \[out\]  Retourne un objet d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) qui représente le document contenant cette position.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)