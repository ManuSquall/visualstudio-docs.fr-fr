---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8941decfb4e64906c57b719df711ce8779df9c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
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

## <a name="requirements"></a>Configuration requise

En-tête : msdbg.h

Namespace : Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll