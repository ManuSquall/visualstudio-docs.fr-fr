---
title: "IDebugProgramHost2::GetHostId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostId"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostId"
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient à l'identificateur de processus d'hébergement de processus ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```c#  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### Paramètres  
 `pdwId`  
 \[in, out\]  Une structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) remplie à l'aide de informations d'identificateur de processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)