---
title: Erreurs de point de rupture (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739217"
---
# <a name="breakpoint-errors"></a>Erreurs de point de rupture
Ce qui suit décrit le processus lorsqu’un point d’arrêt tente de se lier au code, mais échoue.

## <a name="troubleshoot-a-breakpoint-error"></a>Dépanner une erreur de point d’arrêt

1. Le moteur de débogé (DE) envoie un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au gestionnaire de débogique de session (SDM).

2. Le SDM appelle [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2) `ppErrorBP`pour obtenir le point d’erreur.

3. Le SDM appelle [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour obtenir le point d’arrêt en attente à partir duquel le point d’arrêt d’erreur est né.

4. Le SDM appelle [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour obtenir la raison pour laquelle le point d’erreur n’a pas réussi à se lier.

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)
