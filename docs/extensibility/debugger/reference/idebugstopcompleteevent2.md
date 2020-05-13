---
title: IDebugStopCompleteEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719442"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Le moteur de débogé (DE) peut envoyer cet événement optionnel au gestionnaire de débogé de session (SDM) lorsqu’un programme s’est arrêté.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs

Cette interface a été introduite avec Visual Studio 2005. Les rejets antérieurs n’étayaient pas l’arrêt asynchrone.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé par le SDM dans des scénarios multi-processus ou multi-programmes. Lorsqu’un programme envoie un événement d’arrêt au SDM, le SDM demande également l’arrêt d’autres programmes.

L’arrêt est utilisé pour informer asynchronement le SDM qu’un programme a cessé. Informer le SDM est utile pour un moteur de déboguer un interprète, où parfois aucun code ne fonctionne à l’intérieur du programme déboqué, de sorte [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être complété synchronisée. Si un moteur de débogé veut employer cette notification `S_ASYNC_STOP` asynchrone, il doit revenir de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Spécifications

En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
