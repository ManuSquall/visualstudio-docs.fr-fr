---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d080b3073ffc13b90870b40a16a353634f4aa0cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352008"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Le moteur de débogage (dé) peut envoyer cet événement facultatif le Gestionnaire de session de débogage (SDM) lorsqu’un programme s’est arrêté.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs

Cette interface a été introduite avec Visual Studio 2005. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.

- [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée par le SDM dans les scénarios à plusieurs processus ou programme multiples. Lorsqu’un programme envoie un événement d’arrêt pour le SDM, le SDM demande arrêter trop d’autres programmes.

Stop est utilisé pour informer de manière asynchrone le SDM un programme s’est arrêté. Pour informer le SDM est utile pour un moteur de débogage interpréteur, où parfois aucun code n’est en cours d’exécution à l’intérieur de l’élément débogué programmer, donc [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectuée de façon synchrone. Si un moteur de débogage veut employer cette notification asynchrone, elle doit retourner `S_ASYNC_STOP` de [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Configuration requise

En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll