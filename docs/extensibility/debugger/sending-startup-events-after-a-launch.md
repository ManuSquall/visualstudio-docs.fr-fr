---
title: Envoi d’événements de démarrage après un lancement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c9363270593f1d492ec57d119f9a70f8371b0ac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685896"
---
# <a name="send-startup-events-after-a-launch"></a>Envoyer des événements de démarrage après un lancement
Une fois que le moteur de débogage (dé) est attaché au programme, il renvoie une série d’événements de démarrage à la session de débogage.

 Événements de démarrage renvoyées à la session de débogage sont les suivantes :

- Un événement de création de moteur.

- Un événement de création de programme.

- Événements de chargement de module et de la création de thread.

- Un événement complet de chargement, envoyé lorsque le code est chargé et prêt à fonctionner, mais avant l’exécution de n’importe quel code.

  > [!NOTE]
  >  Lorsque cet événement se poursuit, les variables globales sont initialisés et exécuter des routines de démarrage.

- Possible d’autres threads de la création et les événements de chargement de module.

- Un événement de point d’entrée, qui signale que le programme a atteint son point d’entrée principal, tel que **Main** ou `WinMain`. Cet événement n’est pas envoyé en général, si le D’attache à un programme qui est déjà en cours d’exécution.

  Par programmation, l’Allemagne envoie d’abord le Gestionnaire de session de débogage (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface qui représente un événement de création de moteur, suivi d’un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , qui représente un événement de création de programme.

  Ces événements sont généralement suivies par un ou plusieurs [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) les événements de la création de threads et [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) les événements de chargement de module.

  Lorsque le code est chargé et prêt à s’exécuter, mais avant l’exécution de n’importe quel code, l’Allemagne envoie le SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) événement de fin de charge. Pour finir, si le programme n’est pas déjà en cours d’exécution, l’Allemagne envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) événement de point d’entrée, signalant que le programme a atteint son point d’entrée principal et est prêt pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)