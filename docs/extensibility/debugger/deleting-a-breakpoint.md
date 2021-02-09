---
title: Suppression d’un point d’arrêt | Microsoft Docs
description: Découvrez comment le gestionnaire de débogage de session supprime un point d’arrêt en attente et tous les points d’arrêt liés qui y sont liés lorsqu’un point d’arrêt en attente est supprimé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862173"
---
# <a name="deleting-a-breakpoint"></a>Suppression d’un point d’arrêt
Les éléments suivants décrivent le processus de suppression d’un point d’arrêt en attente :

## <a name="deletion-process"></a>Processus de suppression
 Le gestionnaire de débogage de session (SDM) appelle la méthode [IDebugPendingBreakpoint2 ::D supprimable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) pour supprimer le point d’arrêt en attente et tous les points d’arrêt liés qui y sont liés.

> [!NOTE]
> Un point d’arrêt à liaison unique peut également être supprimé par un appel à [IDebugBoundBreakpoint2 ::D supprim](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Voir aussi
- [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
