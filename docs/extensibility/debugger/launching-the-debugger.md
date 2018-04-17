---
title: Lancement du débogueur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="launching-the-debugger"></a>Lancement du débogueur
Lancement du débogueur nécessite l’envoi de la séquence des méthodes et des événements avec leurs attributs corrects.  
  
## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et événements  
  
1.  Le Gestionnaire de session de débogage (SDM) est appelé en choisissant le **déboguer** menu, puis en choisissant **Démarrer**. Consultez [lancement d’un programme](../../extensibility/debugger/launching-a-program.md) pour plus d’informations.  
  
2.  Les appels SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode).  
  
3.  Selon le modèle de processus de débogage du moteur (DE) le `IDebugProgramNodeAttach2::OnAttach` méthode retourne l’une des méthodes suivantes, qui détermine les étapes suivantes.  
  
     Si `S_FALSE` est retourné, le moteur de débogage (DE) est chargé en cours de l’ordinateur virtuel.  
  
     - ou -  
  
     Si `S_OK` est retourné, le DE doit être chargé dans le processus de le SDM. Le SDM puis effectue les tâches suivantes :  
  
    1.  Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de la DE.  
  
    2.  Crée le DE.  
  
    3.  Appels [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  L’envoie DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) pour le SDM avec une `EVENT_SYNC` attribut.  
  
5.  L’envoie DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour le SDM avec une `EVENT_SYNC` attribut.  
  
6.  L’envoie DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour le SDM avec une `EVENT_SYNC` attribut.  
  
7.  L’envoie DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) pour le SDM avec une `EVENT_SYNC` attribut.  
  
8.  L’envoie DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) pour le SDM avec une `EVENT_SYNC` attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de débogueur d’appel](../../extensibility/debugger/calling-debugger-events.md)   
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)