---
title: Création d’un point d’arrêt Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d252f1310c3e251c44525cd94c4d9a2943d8171d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739045"
---
# <a name="create-a-breakpoint"></a>Créer un point d’arrêt
Ce qui suit décrit le processus de création d’un point d’arrêt.

## <a name="methods-in-breakpoint-creation"></a>Méthodes dans la création de points d’arrêt
 Lorsque le module nécessaire pour lier un point d’arrêt est chargé, le gestionnaire de débogé de session (SDM) appelle les méthodes suivantes :

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** est appelé uniquement lorsqu’un utilisateur fait un point d’arrêt à partir de la fenêtre **Breakpoints.**

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Voir aussi
- [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md)
