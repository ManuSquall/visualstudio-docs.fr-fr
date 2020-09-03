---
title: Envoi d’événements de démarrage après un lancement | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713012"
---
# <a name="send-startup-events-after-a-launch"></a>Envoyer des événements de démarrage après un lancement
Une fois que le moteur de débogage (DE) est attaché au programme, il envoie une série d’événements de démarrage à la session de débogage.

 Les événements de démarrage renvoyés à la session de débogage sont les suivants :

- Événement de création de moteur.

- Événement de création de programme.

- Événements de création de thread et de chargement de module.

- Événement de fin de chargement, envoyé lorsque le code est chargé et prêt à être exécuté, mais avant l’exécution de tout code.

  > [!NOTE]
  > Lorsque cet événement se poursuit, les variables globales sont initialisées et les routines de démarrage s’exécutent.

- Autres événements de création de thread et de chargement de module possibles.

- Un événement de point d’entrée, qui indique que le programme a atteint son point d’entrée principal, par exemple **main** ou `WinMain` . Cet événement n’est généralement pas envoyé si le DE est attaché à un programme qui est déjà en cours d’exécution.

  Par programmation, la première adresse un gestionnaire DE débogage de session (SDM) à une interface [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , qui représente un événement de création de moteur, suivi d’un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), qui représente un événement de création de programme.

  Ces événements sont généralement suivis d’un ou plusieurs événements de création de threads [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) et d’événements de chargement de module [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Lorsque le code est chargé et prêt à être exécuté, mais avant l’exécution de tout code, le pour envoie un événement DE chargement [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) de l’exécution du SDM. Enfin, si le programme n’est pas déjà en cours d’exécution, le service DE envoie un événement DE point d’entrée [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , en signalant que le programme a atteint son point d’entrée principal et est prêt pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
