---
title: Quand un point d’arrêt est lié ou devient indépendant | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712330"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quand un point d’arrêt est lié ou non lié
Lorsqu’un point d’arrêt ne peut pas être lié au moment où un appel est effectué à la méthode [IDebugPendingBreakpoint2 :: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , la durée de liaison et l’heure de création du point d’arrêt sont différentes.

## <a name="methods-called"></a>Méthodes appelées
 Le gestionnaire de débogage de session (SDM) appelle les méthodes suivantes :

1. [IDebugEngine2 :: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Le DE retourne un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2 :: Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2 :: virtualiser](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. La méthode [IDebugPendingBreakpoint2 :: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) et retourne S_OK. Le DE envoie un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. Méthodes [IDebugBreakpointBoundEvent2 :: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et [IDebugBreakpointBoundEvent2 :: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) pour vérifier et atteindre les points d’arrêt liés.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
