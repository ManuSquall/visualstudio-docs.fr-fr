---
title: "IDebugProcess2::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProcess2::EnumThreads"
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait une liste de tous les threads en cours de exécution dans le processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) qui contient une liste de tous les threads de tous les programmes dans le processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode énumère les threads qui s'exécutent dans chaque programme puis les combine dans une vue processus des threads.  Un seul thread peut s'exécuter dans plusieurs programmes ; cette méthode énumère ce thread qu'une seule fois.  
  
 Cette méthode présente une liste des threads du processus sans doublons.  Sinon, pour énumérer des threads qui s'exécutent dans un programme particulier, utilisez la méthode d' [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)