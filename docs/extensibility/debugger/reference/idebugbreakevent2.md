---
title: IDebugBreakEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735395"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Cette interface indique au gestionnaire de débopathie de session (SDM) qu’une rupture asynchrone a été réalisée avec succès.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour prendre en charge les pauses utilisateur dans un programme. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette `IDebugEvent2` interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) lorsque l’utilisateur a demandé que le programme soit déboqué pour être mis en pause. Lorsque le programme a été interrompu avec `IDebugBreakEvent2` succès, le DE envoie l’événement. Cet événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il s’est joint au programme en cours de débbugged.

## <a name="remarks"></a>Notes
 Par exemple, un utilisateur peut sélectionner la commande **Break All** sur le menu **Debug** pour sortir d’un programme qui exécute une boucle infinie. Le SDM dit au programme de s’arrêter en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Le DE `IDebugBreakEvent2` envoie quand le programme s’arrête enfin.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
