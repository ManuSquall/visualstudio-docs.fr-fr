---
title: Erreurs de point d’arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31eabde4ae19ae7342188a5d2a16374b9c94afc0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332558"
---
# <a name="breakpoint-errors"></a>Erreurs de point d’arrêt
Ce qui suit décrit le processus lorsqu’un point d’arrêt tente de se lier au code, mais échoue.

## <a name="troubleshoot-a-breakpoint-error"></a>Corriger une erreur de point d’arrêt

1. Le moteur de débogage (dé) envoie une [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) pour le Gestionnaire de session de débogage (SDM).

2. Les appels SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) pour obtenir le point d’arrêt de l’erreur.

3. Les appels SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour obtenir le point d’arrêt en attente dont provenance le point d’arrêt de l’erreur.

4. Les appels SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour obtenir la raison de l’échec le point d’arrêt de l’erreur à lier.

## <a name="see-also"></a>Voir aussi
- [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)