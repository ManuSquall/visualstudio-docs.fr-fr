---
title: Processus Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738247"
---
# <a name="processes"></a>Processus
Dans l’architecture débbugger, un *processus*:

- Est un conteneur pour un ensemble de programmes. Il est étroitement analogue à un processus Windows, qui est un conteneur pour un ensemble de threads.

- Peut s’identifier par nom, identifiant ou identifiant physique.

- Peut énumérer tous les programmes en cours d’exécution (et leurs fils).

- Peut se décrire lui-même, le port dans lequel il est en cours d’exécution, et la machine qui le contient.

- Peut créer un ou plusieurs programmes, mettre fin à l’un des programmes qu’il crée, ou provoquer l’arrêt d’un programme.

- Est représenté par une interface [IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) qui est créée lors du lancement du processus. Un processus est lancé soit par le gestionnaire de déboges de session (SDM) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Le paquet de débaillement peut attacher un moteur de déboguer (DE) à un processus en appelant [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), ce qui signifie que le DE se fixe à tous les programmes possibles en cours d’exécution dans le processus qu’il peut gérer. Par exemple, si le langage courant runtime DE se fixe à un processus, il se fixe uniquement aux programmes qui exécutent le code géré.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Fils](../../extensibility/debugger/threads.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [Paquet Debug](../../extensibility/debugger/debug-package.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
