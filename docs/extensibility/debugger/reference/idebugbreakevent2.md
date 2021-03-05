---
description: Cette interface indique au gestionnaire de débogage de session (SDM) qu’un arrêt asynchrone s’est terminé avec succès.
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dddf2c69cf7ccf221c00e88fc159b762284483ff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143582"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Cette interface indique au gestionnaire de débogage de session (SDM) qu’un arrêt asynchrone s’est terminé avec succès.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour prendre en charge les arrêts utilisateur dans un programme. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quand l’utilisateur a demandé que le programme en cours de débogage soit suspendu. Lorsque le programme a été suspendu, le DE envoie l' `IDebugBreakEvent2` événement. Cet événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="remarks"></a>Notes
 Par exemple, un utilisateur peut sélectionner la commande **arrêter tout** dans le menu **Déboguer** pour sortir d’un programme qui exécute une boucle infinie. Le SDM indique au programme de s’arrêter en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Le DE l’envoi `IDebugBreakEvent2` lorsque le programme s’arrête pour terminer.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
