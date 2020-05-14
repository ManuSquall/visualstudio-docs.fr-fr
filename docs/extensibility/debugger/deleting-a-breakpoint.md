---
title: Suppression d’un point d’arrêt (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738942"
---
# <a name="deleting-a-breakpoint"></a>Suppression d’un point d’arrêt
Ce qui suit décrit le processus lors de la suppression d’un point d’arrêt en attente :

## <a name="deletion-process"></a>Processus de suppression
 Le gestionnaire de débogé de session (SDM) appelle la méthode [IDebugPendingBreakpoint2::Déléte](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) pour supprimer le point d’arrêt en attente et tous les points de rupture liés à partir de lui.

> [!NOTE]
> Un point d’arrêt unique peut également être supprimé par un appel à [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Voir aussi
- [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md)
