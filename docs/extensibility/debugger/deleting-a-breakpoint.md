---
title: Suppression d’un point d’arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7551ee12993780544bbb9c9eb127a9bfb4364e8d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345829"
---
# <a name="deleting-a-breakpoint"></a>Suppression d’un point d’arrêt
La section suivante décrit le processus lors de la suppression d’un point d’arrêt en attente :

## <a name="deletion-process"></a>Processus de suppression
 Le Gestionnaire de session de débogage (SDM) appelle le [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) méthode pour supprimer le point d’arrêt en attente et les points d’arrêt liés liée à partir de celui-ci.

> [!NOTE]
> Un seul point d’arrêt lié peut également être supprimée par un appel à [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Voir aussi
- [Appeler des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)