---
title: Envoi d’événements de démarrage après un lancement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713012"
---
# <a name="send-startup-events-after-a-launch"></a>Envoyer des événements de démarrage après un lancement
Une fois que le moteur de débogé (DE) est attaché au programme, il renvoie une série d’événements de démarrage à la session de débogé.

 Les événements de démarrage renvoyés à la session de débog comprennent:

- Un événement de création de moteur.

- Un événement de création de programme.

- Événements de création de fil et de chargement de module.

- Un événement complet de charge, envoyé lorsque le code est chargé et prêt à s’exécuter, mais avant tout code est exécuté.

  > [!NOTE]
  > Lorsque cet événement se poursuit, les variables globales sont paraméssisées et les routines de démarrage s’exécutent.

- D’autres événements possibles de création de thread et de chargement de module.

- Un événement de point d’entrée, qui indique que **Main** le `WinMain`programme a atteint son point d’entrée principal, comme Main ou . Cet événement n’est généralement pas envoyé si le DE se fixe à un programme qui est déjà en cours d’exécution.

  Sur le programme, le DE envoie d’abord au gestionnaire de débogé de session (SDM) une interface [IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) qui représente un événement de création de moteur, suivi d’un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), qui représente un événement de création de programme.

  Ces événements sont généralement suivis par un ou plusieurs événements de création de [threadS IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) et d’événements de chargement du module [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Lorsque le code est chargé et prêt à s’exécuter, mais avant l’exécution d’un code, le DE envoie au SDM un événement complet de charge [IDebugLoadCompleteEvent2.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Enfin, si le programme n’est pas déjà en cours d’exécution, le DE envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) événement point d’entrée, signalant que le programme a atteint son point d’entrée principal et est prêt pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
