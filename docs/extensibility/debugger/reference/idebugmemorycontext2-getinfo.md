---
title: "IDebugMemoryContext2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetInfo"
helpviewer_keywords: 
  - "Méthode GetInfo"
  - "IDebugMemoryContext2::GetInfo (méthode)"
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une structure de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) qui décrit le contexte.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) qui indiquent les champs de la structure de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) doivent être supérieur.  
  
 `pInfo`  
 \[in, out\]  La structure d' `CONTEXT_INFO` qui est terminée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)