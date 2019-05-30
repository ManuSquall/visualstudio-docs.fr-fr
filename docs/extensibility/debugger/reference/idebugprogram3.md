---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cfc29f300bc9f28f857424a7a91b4b6bfd3bf82
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331530"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Cette interface représente un programme qui s’exécute dans un processus et l’étend [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) en fournissant des informations sur le thread.

## <a name="syntax"></a>Syntaxe

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le Gestionnaire de session de débogage (SDM) implémente également cette interface pour fournir des informations à [attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement retourne cette interface pour un nouveau programme. Cette interface est également utilisée en tant que paramètre pour de nombreuses méthodes sur plusieurs interfaces.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgram3`.

|Méthode|Description|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Exécute le programme. Le thread est retourné pour fournir les informations du débogueur threads sur lesquels l’utilisateur visualise lors de l’exécution.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Un programme est un conteneur de thread en cours d’exécution dans une architecture particulière de l’exécution, pendant un processus est constitué d’un ou plusieurs programmes.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)