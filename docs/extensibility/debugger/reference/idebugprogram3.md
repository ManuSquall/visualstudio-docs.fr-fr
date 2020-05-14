---
title: IDebugProgram3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722643"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Cette interface représente un programme qui s’exécute dans un processus et étend [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md) en fournissant des informations de thread.

## <a name="syntax"></a>Syntaxe

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le gestionnaire de débogé de session (SDM) implémente également cette interface pour fournir des informations à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 [L’événement IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) renvoie cette interface pour un nouveau programme. Cette interface est également utilisée comme paramètre pour de nombreuses méthodes sur plusieurs interfaces.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProgram3`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Exécute le programme. Le thread est retourné pour donner aux informations de débagé sur le thread que l’utilisateur affiche lors de l’exécution.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Un programme est un conteneur de fil fonctionnant dans une architecture de temps d’exécution particulière, tandis qu’un processus est composé d’un ou plusieurs programmes.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
