---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722719"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Cette interface représente un programme qui s’exécute dans un processus.

## <a name="syntax"></a>Syntaxe

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le gestionnaire de débogage de session (SDM) implémente également cette interface pour fournir des informations à [attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 L’événement [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) retourne cette interface pour un nouveau programme. Cette interface est également utilisée comme paramètre pour de nombreuses méthodes sur plusieurs interfaces.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgram2` .

|Méthode|Description|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Énumère les threads qui s’exécutent dans ce programme.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtient le nom du programme.|
|[GetProcess,](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtient le processus dans lequel ce programme s’exécute.|
|[Terminer](../../../extensibility/debugger/reference/idebugprogram2-terminate.md).|Met fin à ce programme.|
|[Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Attache à ce programme.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Détermine si un moteur de débogage (DE) peut se détacher du programme.|
|[Détacher](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Détache le débogueur de ce programme.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtient un identificateur global unique pour ce programme.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtient les propriétés du programme.|
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Poursuit l’exécution de ce programme à partir d’un état arrêté. Tout état d’exécution précédent est effacé.|
|[Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Poursuit l’exécution de ce programme à partir d’un état arrêté. Tout état d’exécution précédent est conservé.|
|[Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Exécute une étape.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Demande que ce programme arrête l’exécution la prochaine fois que l’un de ses threads exécute le code.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtient le nom et l’identificateur du moteur de débogage qui exécute ce programme.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Énumère les contextes de code pour une position donnée dans un fichier source.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtient les octets de mémoire pour ce programme.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtient le flux de code machine pour ce programme ou une partie de ce programme.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Énumère les modules que ce programme a chargés et est en cours d’exécution.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtient la mise à jour de modifier & Continuer (ENC) pour ce programme.<br /><br /> Un moteur de débogage personnalisé n’implémente pas cette méthode (il doit toujours retourner `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Énumère les chemins de code de ce programme.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Écrit un dump dans un fichier.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Un programme est un conteneur de thread s’exécutant dans une architecture Runtime particulière, tandis qu’un processus est constitué d’un ou de plusieurs programmes.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
