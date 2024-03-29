---
title: Création d’un point d’arrêt | Microsoft Docs
description: En savoir plus sur les appels de méthode que le gestionnaire de débogage de session effectue lorsque le module nécessaire pour lier un point d’arrêt est chargé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 719a003e3dd46f46a0bf30642bed4b428d0956f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067996"
---
# <a name="create-a-breakpoint"></a>Créer un point d’arrêt
Les éléments suivants décrivent le processus de création d’un point d’arrêt.

## <a name="methods-in-breakpoint-creation"></a>Méthodes de création de point d’arrêt
 Lorsque le module nécessaire pour lier un point d’arrêt est chargé, le gestionnaire de débogage de session (SDM) appelle les méthodes suivantes :

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** est appelé uniquement lorsqu’un utilisateur crée un point d’arrêt à partir de la fenêtre **points d’arrêt** .

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Voir aussi
- [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
