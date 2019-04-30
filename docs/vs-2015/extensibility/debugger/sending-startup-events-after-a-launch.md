---
title: Envoi d’événements de démarrage après un lancement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436664"
---
# <a name="sending-startup-events-after-a-launch"></a>Envoi d’événements de démarrage après un lancement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une fois que le moteur de débogage (dé) est attaché au programme, il renvoie une série d’événements de démarrage à la session de débogage.  
  
 Événements de démarrage renvoyées à la session de débogage sont les suivants :  
  
- Un événement de création de moteur.  
  
- Un événement de création de programme.  
  
- Événements de chargement de module et de la création de thread.  
  
- Un événement de fin de chargement envoyé lorsque le code est chargé et prêt à fonctionner, mais avant l’exécution de code  
  
  > [!NOTE]
  > Lorsque cet événement se poursuit, les variables globales sont initialisés et exécuter des routines de démarrage.  
  
- Possible d’autres threads de la création et les événements de chargement de module.  
  
- Un événement de point d’entrée, qui signale que le programme a atteint son point d’entrée principal, tel que **Main** ou `WinMain`. Cet événement n’est pas envoyé en général, si le D’attache à un programme qui est déjà en cours d’exécution.  
  
  Par programmation, l’Allemagne envoie d’abord le Gestionnaire de session de débogage (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface qui représente un événement de création de moteur, suivi d’un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , qui représente un événement de création de programme.  
  
  Cela est généralement suivi d’un ou plusieurs [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) les événements de la création de threads et [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) les événements de chargement de module.  
  
  Lorsque le code est chargé et prêt à s’exécuter, mais avant l’exécution de n’importe quel code, l’Allemagne envoie le SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) événement de fin de charge. Pour finir, si le programme n’est pas déjà en cours d’exécution, l’Allemagne envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) événement de point d’entrée, signalant que le programme a atteint son point d’entrée principal et est prêt pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
