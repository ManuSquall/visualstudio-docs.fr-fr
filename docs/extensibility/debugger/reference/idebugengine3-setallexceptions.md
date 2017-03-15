---
title: "IDebugEngine3::SetAllExceptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetAllExceptions"
helpviewer_keywords: 
  - "IDebugEngine3::SetAllExceptions"
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine3::SetAllExceptions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode définit l'état de toutes les exceptions en attente.  
  
## Syntaxe  
  
```cpp  
HRESULT SetAllExceptions(  
   EXCEPTION_STATE dwState  
);  
```  
  
```c#  
int SetAllExceptions(  
   enum_EXCEPTION_STATE dwState  
);  
```  
  
#### Paramètres  
 `dwState`  
 \[in\]  L'une des valeurs d' [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)