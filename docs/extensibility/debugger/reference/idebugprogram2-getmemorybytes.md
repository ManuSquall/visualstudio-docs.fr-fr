---
title: "IDebugProgram2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère les octets de mémoire occupés par le programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Paramètres  
 `ppMemoryBytes`  
 \[out\]  Retourne un objet d' [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) qui représente les octets de mémoire du programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les octets de mémoire représentés par l'objet d' [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) est pour l'image de programme en mémoire et non toute mémoire allouée lorsque le programme a été exécuté.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)