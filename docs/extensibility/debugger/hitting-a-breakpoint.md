---
title: Atteindre un point d’arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d95abd66f248ca994d7712f1bf51519022de9d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344046"
---
# <a name="hit-a-breakpoint"></a>Atteindre un point d’arrêt
La section suivante décrit le processus lorsque le moteur de débogage (dé) atteint un point d’arrêt pendant l’exécution ou pas à pas :

## <a name="troubleshoot-a-hit-breakpoint"></a>Résoudre les problèmes d’un point d’arrêt d’accès

1. L’envoie DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface comme une **EVENT_SYNC_STOP**.

2. Appelle le Gestionnaire de session de débogage (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir le point d’arrêt a été atteint.

## <a name="see-also"></a>Voir aussi
- [Appeler des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)