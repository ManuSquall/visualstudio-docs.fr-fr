---
title: Atteindre un point d’arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1286af8222703028d5a8a1bd2dbb0d990ca7e30c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889903"
---
# <a name="hit-a-breakpoint"></a>Atteindre un point d’arrêt
La section suivante décrit le processus lorsque le moteur de débogage (dé) atteint un point d’arrêt pendant l’exécution ou pas à pas :

## <a name="troubleshoot-a-hit-breakpoint"></a>Résoudre les problèmes d’un point d’arrêt d’accès

1. L’envoie DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface comme une **EVENT_SYNC_STOP**.

2. Appelle le Gestionnaire de session de débogage (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir le point d’arrêt a été atteint.

## <a name="see-also"></a>Voir aussi
- [Appeler des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)