---
title: "IDebugDocument2::GetDocumentClassID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
helpviewer_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient l'identificateur de classe du document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```c#  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### Paramètres  
 `pclsid`  
 \[out\]  Retourne un GUID qui est l'ID de classe du document.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La classe GUID peut être utilisé pour instancier différentes classes qui représente un document.  
  
## Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)