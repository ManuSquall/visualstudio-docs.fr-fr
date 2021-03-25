---
description: Le moteur DE débogage (DE) peut envoyer cet événement facultatif au gestionnaire de débogage de session (SDM) lorsqu’un programme s’est arrêté.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087143"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Le moteur DE débogage (DE) peut envoyer cet événement facultatif au gestionnaire de débogage de session (SDM) lorsqu’un programme s’est arrêté.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs

Cette interface a été introduite avec Visual Studio 2005. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.

- L' [arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé par le SDM dans des scénarios à plusieurs processus ou à plusieurs programmes. Lorsqu’un programme envoie un événement d’arrêt au SDM, le SDM demande également l’arrêt d’autres programmes.

L’arrêt est utilisé pour informer le SDM de manière asynchrone qu’un programme s’est arrêté. L’information du SDM est utile pour un moteur de débogage de l’interpréteur, où aucun code n’est parfois exécuté à l’intérieur du programme débogué. par conséquent, l' [arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectué de façon synchrone. Si un moteur de débogage souhaite utiliser cette notification asynchrone, il doit retourner `S_ASYNC_STOP` à partir de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Spécifications

En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
