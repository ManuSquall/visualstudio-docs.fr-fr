---
title: "IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si un processus peut être terminé.  
  
## Syntaxe  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Paramètres  
 `pProcess`  
 \[in\]  un objet d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus à terminer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `S_FALSE` si le moteur ne peut pas arrêter le processus, par exemple, l'accès est refusé.  
  
## Notes  
 Si cette méthode retourne `S_OK`, elle la méthode d' [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) peut être appelée pour terminer en fait le processus.  
  
## Voir aussi  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)