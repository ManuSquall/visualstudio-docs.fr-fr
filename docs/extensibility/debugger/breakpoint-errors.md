---
title: Erreurs de point d’arrêt | Microsoft Docs
description: En savoir plus sur le processus lorsqu’un point d’arrêt tente de se lier au code, mais échoue et comment résoudre les erreurs de point d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12e8efc7fc110f3f5c20c92d97cf3692094ef6aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055234"
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
