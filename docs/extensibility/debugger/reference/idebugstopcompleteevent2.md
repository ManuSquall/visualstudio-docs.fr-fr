---
title: IDebugStopCompleteEvent2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119248"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Le moteur de débogage (DE) peut envoyer cet événement facultatif pour le Gestionnaire de session de débogage (SDM) lorsqu’un programme s’est arrêté.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs

Cette interface a été introduite avec Visual Studio 2005. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.

[Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée par le SDM dans plusieurs processus ou programme plusieurs scénarios. Lorsqu’un programme envoie un événement d’arrêt pour le SDM, le SDM demande arrêter trop des autres programmes.

Stop est utilisé pour informer de façon asynchrone le SDM un programme s’est arrêté. Pour informer le SDM est utile pour un moteur de débogage interpréteur, où parfois aucun code n’est en cours d’exécution à l’intérieur de l’élément débogué de programme, donc [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectuée de façon synchrone. Si un moteur de débogage veut employer cette notification asynchrone, elle doit retourner `S_ASYNC_STOP` de [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Spécifications

En-tête : msdbg.h

Namespace : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll