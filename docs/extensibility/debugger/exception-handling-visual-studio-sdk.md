---
title: Manipulation d’exception (Visual Studio SDK) Microsoft Docs
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
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738759"
---
# <a name="exception-handling-visual-studio-sdk"></a>Manipulation d’exception (Visual Studio SDK)
Ce qui suit décrit le processus qui se produit lorsque des exceptions sont jetées.

## <a name="exception-handling-process"></a>Processus de traitement des exceptions

1. Lorsqu’une exception est lancée pour la première fois, mais avant qu’elle ne soit traitée par le gestionnaire d’exception dans le programme étant débogé, le moteur de débogé (DE) envoie un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) au gestionnaire de débogé de session (SDM) comme un événement d’arrêt. Le `IDebugExceptionEvent2` est envoyé si seulement les paramètres pour l’exception (spécifié dans la boîte de dialogue Exceptions dans le paquet de débogs) spécifient que l’utilisateur veut s’arrêter sur les notifications d’exception de première chance.

2. Le SDM appelle [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pour obtenir la propriété d’exception.

3. Le paquet de débacher appelle [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer quelles options présenter à l’utilisateur.

4. Le paquet de débogs demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.

5. Si l’utilisateur choisit de continuer, le SDM appelle [IDebugExceptionEvent2:CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Si la méthode revient S_OK, appelle [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -ou-

         Si la méthode revient S_FALSE, le programme qui est déboqué a une deuxième chance de gérer l’exception.

6. Si le programme étant déboché n’a pas de gestionnaire `IDebugExceptionEvent2` pour une exception de deuxième chance, le DE envoie un à la SDM comme **EVENT_SYNC_STOP**.

7. Le paquet de débogs demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.

8. Le paquet de débacher appelle [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer quelles options présenter à l’utilisateur.

9. Le paquet de débogs demande à l’utilisateur comment gérer l’exception en ouvrant une case de dialogue d’exception de seconde chance.

10. Si la méthode renvoie S_OK, appelle `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Voir aussi
- [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md)
