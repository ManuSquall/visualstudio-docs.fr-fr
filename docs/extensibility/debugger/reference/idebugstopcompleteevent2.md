---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39da50c17d4d4b8b02390e0d2960d5696b93b1f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932890"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Le moteur de débogage (dé) peut envoyer cet événement facultatif le Gestionnaire de session de débogage (SDM) lorsqu’un programme s’est arrêté.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs

Cette interface a été introduite avec Visual Studio 2005. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.

[Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée par le SDM dans les scénarios à plusieurs processus ou programme multiples. Lorsqu’un programme envoie un événement d’arrêt pour le SDM, le SDM demande arrêter trop d’autres programmes.

Stop est utilisé pour informer de manière asynchrone le SDM un programme s’est arrêté. Pour informer le SDM est utile pour un moteur de débogage interpréteur, où parfois aucun code n’est en cours d’exécution à l’intérieur de l’élément débogué programmer, donc [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectuée de façon synchrone. Si un moteur de débogage veut employer cette notification asynchrone, elle doit retourner `S_ASYNC_STOP` de [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Spécifications

En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll