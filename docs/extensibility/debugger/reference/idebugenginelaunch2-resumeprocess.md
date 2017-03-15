---
title: "IDebugEngineLaunch2::ResumeProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineLaunch2::ResumeProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Les synthèses traitent l'exécution.  
  
## Syntaxe  
  
```cpp#  
HRESULT ResumeProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int ResumeProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Paramètres  
 `pProcess`  
 \[in\]  un objet d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus à continuer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée une fois qu'un processus a été lancé par un appel à la méthode d' [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) .  
  
## Voir aussi  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)