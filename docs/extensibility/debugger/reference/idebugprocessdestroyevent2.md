---
title: IDebugProcessDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a0e0c854a611f222958361ef429fddf09f0cf5e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348911"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Cette interface est envoyée lorsqu’un processus est arrêté, s’arrête anormalement ou est détaché de.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) ou le fournisseur de port personnalisé implémentent cette interface pour signaler qu’un processus a été arrêté. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 L’Allemagne ou le fournisseur de port personnalisé crée et envoie cet objet d’événement pour signaler l’arrêt d’un processus. Le D’envoie cet événement à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage. Le fournisseur de port personnalisé envoie cet événement à l’aide de la [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)