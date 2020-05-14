---
title: Frapper un point d’arrêt (fr) Microsoft Docs
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
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738564"
---
# <a name="hit-a-breakpoint"></a>Atteindre un point d’arrêt
La section suivante décrit le processus lorsque le moteur de déboguer (DE) heurte un point d’arrêt en cours d’exécution ou en marchant :

## <a name="troubleshoot-a-hit-breakpoint"></a>Dépanner un point d’arrêt frappé

1. Le DE envoie une interface [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) comme **une EVENT_SYNC_STOP**.

2. Le gestionnaire de déboptillement de session (SDM) appelle [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir le point d’arrêt qui a été touché.

## <a name="see-also"></a>Voir aussi
- [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md)
