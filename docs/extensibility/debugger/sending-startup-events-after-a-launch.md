---
title: "Envoi d’événements de démarrage après un lancement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sending-startup-events-after-a-launch"></a>Envoi d’événements de démarrage après un lancement
Une fois que le moteur de débogage (DE) est attaché au programme, il renvoie une série d’événements de démarrage à la session de débogage.  
  
 Événements de démarrage renvoyés à la session de débogage sont les suivantes :  
  
-   Événement de création d’un moteur.  
  
-   Événement de création d’un programme.  
  
-   Événements de chargement de module et de la création du thread.  
  
-   Un événement complet de chargement, envoyé lorsque le code est chargé et prêt à s’exécuter, mais avant l’exécution de code  
  
    > [!NOTE]
    >  Lorsque cet événement se poursuit, les variables globales sont initialisés et exécuter des routines de démarrage.  
  
-   Possible d’autres événements de chargement de module et de la création du thread.  
  
-   Un événement de point d’entrée, qui signale que le programme a atteint son point d’entrée principal, tel que **principal** ou `WinMain`. Cet événement n’est pas envoyé en général, si le D’attache un programme qui est déjà en cours d’exécution.  
  
 Par programme, le D’envoie d’abord le Gestionnaire de session de débogage (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface qui représente un événement de création de moteur, suivi d’un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , qui représente un événement de création de programme.  
  
 Cela est généralement suivi d’un ou plusieurs [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) les événements de la création de threads et [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) les événements de chargement de module.  
  
 Lorsque le code est chargé et prêt à s’exécuter, mais avant l’exécution de code, le D’envoie le SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) charge complète des événements. Pour finir, si le programme n’est pas déjà en cours d’exécution, le D’envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) événement de point d’entrée, signalant que le programme a atteint son point d’entrée principal et est prêt pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)