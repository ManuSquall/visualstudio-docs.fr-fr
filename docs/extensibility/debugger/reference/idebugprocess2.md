---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "Interface de IDebugProcess2"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un processus s'exécutant sur un port.  Si le port est le port local, puis `IDebugProcess2` représente habituellement un processus physique sur l'ordinateur local.  
  
## Syntaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par un fournisseur de port pour gérer des programmes en tant que groupe.  cette interface doit être implémentée par le fournisseur de port.  
  
 Un moteur de débogage implémente également cette interface s'il prend en charge exécuter un programme via [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## Remarques pour les appelants  
 Cette interface est appelée principalement par le gestionnaire de débogage de \(SDM\) connexion pour interagir avec un groupe de programmes identifiés dans ce processus.  
  
 appelez [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../Topic/IDebugPort2::GetProcess.md) pour obtenir cette interface.  Cette interface est également retourné en appelant `IDebugEngineLaunch2::LaunchSuspended`.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProcess2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|obtient une description du processus.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|énumère les programmes qui sont contenus dans ce processus.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|obtient le titre, le nom convivial, ou le nom de fichier du processus.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtient l'instance d'un serveur d'ordinateur que ce processus s'exécute.|  
|[Terminer](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Met fin au processus.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|S'attache au processus.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|détermine si le SDM peut détacher le processus.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|détache le débogueur du processus.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|obtient l'identificateur de processus système.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|obtient un identificateur global unique pour ce processus.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[DÉSAPPROUVÉ\]|Obtient le nom de la session qui sont traduits dans le processus.<br /><br /> \[DÉSAPPROUVÉ.  DEVRAIT TOUJOURS RENVOYER `E_NOTIMPL`.\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Énumère les threads en cours de exécution dans le processus.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Requêtes qui le programme suivant exécutant le code dans cet arrêt du processus.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtient le port que ce processus s'exécute.|  
  
## Notes  
 `IDebugProcess2` contient une ou plusieurs interfaces d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)