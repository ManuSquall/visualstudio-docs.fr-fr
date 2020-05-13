---
title: IDebugProcessdestroyEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d7c93c1e5811ec3aed5d44f3c306de1c09cced9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723444"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Cette interface est envoyée lorsqu’un processus est terminé, sort atypiquement, ou est détaché.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) ou le fournisseur de port personnalisé implémentent cette interface pour signaler qu’un processus a été terminé. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE ou le fournisseur de port personnalisé crée et envoie cet objet d’événement pour signaler la fin d’un processus. Le DE envoie cet événement en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débotage. Le fournisseur de porto personnalisé envoie cet événement à l’aide de l’interface [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
