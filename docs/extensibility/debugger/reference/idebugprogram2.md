---
title: IDebugProgram2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722719"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Cette interface représente un programme qui fonctionne dans un processus.

## <a name="syntax"></a>Syntaxe

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le gestionnaire de débogé de session (SDM) implémente également cette interface pour fournir des informations à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 [L’événement IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) renvoie cette interface pour un nouveau programme. Cette interface est également utilisée comme paramètre pour de nombreuses méthodes sur plusieurs interfaces.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProgram2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Énumère les fils qui sont en cours d’exécution dans ce programme.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtient le nom du programme.|
|[GetProcess (en)](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtient le processus que ce programme est en cours d’exécution.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Termine ce programme.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Attache à ce programme.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Détermine si un moteur de débogé (DE) peut se détacher du programme.|
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Détache le débbuggeur de ce programme.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtient un identifiant unique à l’échelle mondiale pour ce programme.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtient des propriétés de programme.|
|[Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue à exécuter ce programme à partir d’un état arrêté. Tout état d’exécution précédent est effacé.|
|[Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue à exécuter ce programme à partir d’un état arrêté. Tout état d’exécution antérieur est préservé.|
|[Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Effectue une étape.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Demande que ce programme cesse l’exécution la prochaine fois qu’un de ses threads exécute le code.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtient le nom et l’identifiant du moteur de débogé (DE) en cours d’exécution de ce programme.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Énumère les contextes de code pour une position donnée dans un fichier source.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtient les octets de mémoire pour ce programme.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtient le flux de démontage pour ce programme ou une partie de ce programme.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Énumère les modules que ce programme a chargés et exécute.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtient la mise à jour Edit and Continue (ENC) pour ce programme.<br /><br /> Un moteur de débogé personnalisé ne met `E_NOTIMPL`pas en œuvre cette méthode (il doit toujours revenir ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Énumère les chemins de code de ce programme.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Écrit une décharge à un fichier.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Un programme est un conteneur de fil fonctionnant dans une architecture de temps d’exécution particulière, tandis qu’un processus est composé d’un ou plusieurs programmes.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
