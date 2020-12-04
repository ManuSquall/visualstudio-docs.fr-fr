---
title: Atteindre un point d’arrêt | Microsoft Docs
description: Cet article décrit le processus qui a lieu lorsque le moteur de débogage atteint un point d’arrêt lors de l’exécution ou du pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560848"
---
# <a name="hit-a-breakpoint"></a>Atteindre un point d’arrêt
La section suivante décrit le processus lorsque le moteur DE débogage atteint un point d’arrêt lors de l’exécution ou du pas à pas :

## <a name="troubleshoot-a-hit-breakpoint"></a>Résoudre les problèmes d’un point d’arrêt

1. Le DE envoie une interface [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) en tant que **EVENT_SYNC_STOP**.

2. Le gestionnaire de débogage de session (SDM) appelle [IDebugBreakpointEvent2 ::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour récupérer le point d’arrêt qui a été atteint.

## <a name="see-also"></a>Voir aussi
- [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
