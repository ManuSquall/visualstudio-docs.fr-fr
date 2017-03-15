---
title: "IDebugProgramDestroyEventFlags2::GetFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFlags"
  - "IDebugProgramDestroyEventFlags2::GetFlags"
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgramDestroyEventFlags2::GetFlags
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère le programme détruisent des balises.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetFlags(  
   PROGRAM_DESTROY_FLAGS* pdwFlags  
);  
```  
  
```c#  
public int GetFlags(  
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags  
);  
```  
  
#### Paramètres  
 `pdwFlags`  
 \[out\]  représente le programme détruisent des balises.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)   
 [PROGRAM\_DESTROY\_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)