---
title: "IDebugCoreServer3::DisableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::DisableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::DisableAutoAttach"
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugCoreServer3::DisableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Désactive l'attachement automatique pour tous les moteurs de débogage associés à ce serveur.  
  
## Syntaxe  
  
```cpp#  
HRESULT DisableAutoAttach(  
   void  
);  
```  
  
```c#  
int DisableAutoAttach();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)