---
title: IDebugProcess2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723798"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Cette interface représente un processus fonctionnant sur un port. Si le port est le `IDebugProcess2` port local, alors représente généralement un processus physique sur la machine locale.

## <a name="syntax"></a>Syntaxe

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un fournisseur de ports personnalisé pour gérer les programmes en tant que groupe. Cette interface doit être mise en œuvre par le fournisseur du port.

 Un moteur de débogé implémente également cette interface s’il prend en charge le lancement d’un programme par [Le biais de LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée principalement par le gestionnaire de débogé de session (SDM) afin d’interagir avec un groupe de programmes identifiés dans ce processus.

 Appelez [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) pour obtenir cette interface. Cette interface est également `IDebugEngineLaunch2::LaunchSuspended`retournée en appelant .

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProcess2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtient une description du processus.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Énumère les programmes qui sont contenus dans ce processus.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtient le titre, le nom amical, ou le nom de fichier du processus.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtient l’exemple d’un serveur de machine ce processus est en cours d’exécution sur.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Termine le processus.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Attache au processus.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Détermine si le SDM peut détacher le processus.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Détache le débbuggeur du processus.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtient l’identifiant de processus de système.|
|[GetProcessId (en)](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtient un identifiant unique à l’échelle mondiale pour ce processus.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DÉPRÉCIÉ]|Obtient le nom de la session qui est débogage du processus.<br /><br /> [DÉPRÉCIÉ. DEVRAIT TOUJOURS `E_NOTIMPL`REVENIR .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Énumère les fils en cours d’exécution dans le processus.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Demande que le prochain programme exécutant le code dans ce processus s’arrête.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtient le port que ce processus est en cours d’exécution sur.|

## <a name="remarks"></a>Notes
 Une `IDebugProcess2` contient une ou plusieurs interfaces [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess (en)](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess (en)](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Suivant](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
