---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187966"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un processus en cours d’exécution sur un port. Si le port est le port local, `IDebugProcess2` représente généralement un processus physique sur l’ordinateur local.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par un fournisseur de ports personnalisé pour gérer les programmes en tant que groupe. Cette interface doit être implémentée par le fournisseur de port.  
  
 Un moteur de débogage implémente également cette interface s’il prend en charge le lancement d’un programme par le biais de [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Cette interface est appelée principalement par le gestionnaire de débogage de session (SDM) pour interagir avec un groupe de programmes identifiés dans ce processus.  
  
 Appelez [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) pour accéder à cette interface. Cette interface est également retournée en appelant `IDebugEngineLaunch2::LaunchSuspended` .  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcess2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtient une description du processus.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Énumère les programmes contenus dans ce processus.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtient le titre, le nom convivial ou le nom de fichier du processus.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtient l’instance d’un serveur de machine sur lequel ce processus s’exécute.|  
|[Terminer](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).|Met fin au processus.|  
|[Attacher](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Attache au processus.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Détermine si le SDM peut détacher le processus.|  
|[Détacher](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Détache le débogueur du processus.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtient l’identificateur de processus système.|  
|[GetProcessID,](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtient un identificateur global unique pour ce processus.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> DÉCONSEILLÉ|Obtient le nom de la session qui débogue le processus.<br /><br /> Déconseillé. DOIT toujours retourner `E_NOTIMPL` .]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Énumère les threads en cours d’exécution dans le processus.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Demande que le prochain programme qui exécute le code dans ce processus s’arrête.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtient le port sur lequel ce processus s’exécute.|  
  
## <a name="remarks"></a>Notes  
 Un `IDebugProcess2` contient une ou plusieurs interfaces [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess,](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess,](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Situé](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
