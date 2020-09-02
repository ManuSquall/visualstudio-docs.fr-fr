---
title: Erreurs de point d’arrêt | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739217"
---
# <a name="breakpoint-errors"></a>Erreurs de point d’arrêt
Les éléments suivants décrivent le processus lorsqu’un point d’arrêt tente de se lier à du code mais échoue.

## <a name="troubleshoot-a-breakpoint-error"></a>Résoudre une erreur de point d’arrêt

1. Le moteur DE débogage (DE) envoie un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au gestionnaire de débogage de session (SDM).

2. Le SDM appelle [IDebugBreakpointErrorEvent2 :: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) pour recevoir le point d’arrêt d’erreur.

3. Le SDM appelle [IDebugErrorBreakpoint2 :: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour recevoir le point d’arrêt en attente d’origine du point d’arrêt de l’erreur.

4. Le SDM appelle [IDebugErrorBreakpoint2 :: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour connaître la raison pour laquelle le point d’arrêt de l’erreur n’a pas pu être lié.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
