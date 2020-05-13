---
title: Lorsqu’un point d’arrêt se lie ou devient inbound . Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712330"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Lorsqu’un point d’arrêt se lie ou devient non lié
Lorsqu’un point d’arrêt ne peut pas être lié au moment où un appel est fait à [l’IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) méthode, le temps de liaison et de créer le temps de l’arrêt sont différents.

## <a name="methods-called"></a>Méthodes appelées
 Le gestionnaire de débogé de session (SDM) appelle les méthodes suivantes :

1. [IDebugEngine2::CréerPendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Le DE retourne un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. [L’IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) méthode et retourne S_OK. Le DE envoie un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) et [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) méthodes pour vérifier et pour obtenir les points de rupture liés.

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)
