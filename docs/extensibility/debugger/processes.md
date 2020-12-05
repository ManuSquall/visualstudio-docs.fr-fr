---
title: Processus | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un processus dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a707d62443004795824c8bd437c29802635cf41
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606500"
---
# <a name="processes"></a>Processus
Dans l’architecture du débogueur, un *processus*:

- Est un conteneur pour un ensemble de programmes. Il est étroitement analogue à un processus Windows, qui est un conteneur pour un ensemble de threads.

- Peut s’identifier à l’aide d’un nom, d’un identificateur ou d’un identificateur physique.

- Peut énumérer tous les programmes en cours d’exécution (et leurs threads).

- Peut se décrire lui-même, le port dans lequel il s’exécute et l’ordinateur qui le contient.

- Peut créer un ou plusieurs programmes, terminer l’un des programmes qu’il crée ou provoquer l’arrêt d’un programme.

- Est représenté par une interface [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , qui est créée lorsque le processus est lancé. Un processus est lancé par le gestionnaire de débogage de session (SDM) ou par [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Le package de débogage peut attacher un moteur de débogage (DE) à un processus en appelant [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), ce qui signifie que le se lie à tous les programmes possibles qui s’exécutent dans le processus qu’il peut gérer. Par exemple, si le common language runtime DE s’attache à un processus, il s’attache uniquement aux programmes qui exécutent le code managé.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Package de débogage](../../extensibility/debugger/debug-package.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attacher](../../extensibility/debugger/reference/idebugprocess2-attach.md)
