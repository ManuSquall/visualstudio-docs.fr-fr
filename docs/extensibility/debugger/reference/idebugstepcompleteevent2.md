---
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be6568e84157c8d042113fe6f2f86b2cf288005
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868637"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour le Gestionnaire de session de débogage (SDM) lorsque le programme en cours de débogage termine un pas à pas détaillé, pas à pas principal ou une étape en dehors d’une ligne de code source ou d’une instruction ou d’instruction.

## <a name="syntax"></a>Syntaxe

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour signaler l’achèvement d’une opération de l’étape. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler l’achèvement d’une opération de l’étape. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="remarks"></a>Notes
 Une fois l’étape terminée, le programme en cours de débogage est suspendu une fois de plus, et met à jour de l’IDE toutes ses fenêtres.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)