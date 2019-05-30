---
title: Threads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9759536e1b27018a3361bbb723b4cde0f88269e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333659"
---
# <a name="threads"></a>Threads
Dans l’architecture du débogueur, une *thread*:

- Est l’unité fondamentale de calcul. Un thread exécute séquentiellement ses instructions dans le contexte d’une seule pile d’appels, déplacement à partir du contexte d’un code à l’autre.

- Peut identifier lui-même et le programme, dans qu'il est en cours d’exécution. Threads peuvent être nommés, suspendus et repris. Un thread peut également énumérer ses frames de pile associée et, sous certaines conditions, peut être déplacé vers un autre frame de pile. Étant donné le contexte d’un frame de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread a des propriétés, telles que d’un compteur de suspension, qui peut être affiché dans le **Threads** fenêtre de l’IDE.

- Est représenté par un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, généralement créé par un moteur de débogage (dé) ou d’une machine virtuelle en raison de l’exécution d’un programme.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Frames de pile](../../extensibility/debugger/stack-frames.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)