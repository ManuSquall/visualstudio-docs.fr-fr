---
title: Gestion des exceptions (kit de développement logiciel Visual Studio) | Microsoft Docs
description: En savoir plus sur le processus qui se produit lorsque des exceptions sont levées. Cet article décrit toutes les étapes nécessaires.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af5dc1007a4624a24bef59dd822f6e9fe3861551
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559652"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestion des exceptions (kit de développement logiciel Visual Studio)
Les éléments suivants décrivent le processus qui se produit lorsque des exceptions sont levées.

## <a name="exception-handling-process"></a>Processus de gestion des exceptions

1. Quand une exception est levée pour la première fois, mais avant qu’elle ne soit gérée par le gestionnaire d’exceptions dans le programme en cours de débogage, le moteur DE débogage (DE) envoie un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) vers le gestionnaire de débogage de session (SDM) comme événement d’arrêt. `IDebugExceptionEvent2`Est envoyé si seuls les paramètres de l’exception (spécifiés dans la boîte de dialogue exceptions dans le package de débogage) spécifient que l’utilisateur souhaite s’arrêter sur les notifications d’exceptions de première chance.

2. Le SDM appelle [IDebugExceptionEvent2 :: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pour récupérer la propriété de l’exception.

3. Le package de débogage appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options à présenter à l’utilisateur.

4. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.

5. Si l’utilisateur choisit de continuer, le SDM appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Si la méthode retourne S_OK, appelle [IDebugExceptionEvent2 ::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         - ou -

         Si la méthode retourne S_FALSE, le programme en cours de débogage reçoit une seconde chance de gérer l’exception.

6. Si le programme en cours de débogage n’a pas de gestionnaire pour une exception de deuxième chance, le DE envoie un `IDebugExceptionEvent2` au SDM en tant que **EVENT_SYNC_STOP**.

7. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.

8. Le package de débogage appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options à présenter à l’utilisateur.

9. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de deuxième chance.

10. Si la méthode retourne S_OK, appelle `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Voir aussi
- [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
