---
title: Lancement du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25098b58dd615cabca67e96f0d1848d1f0e8c66d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689120"
---
# <a name="launch-the-debugger"></a>Lancer le débogueur
Lancement du débogueur nécessite l’envoi de la séquence des méthodes et des événements avec leurs attributs corrects.

## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et événements

1.  Le Gestionnaire de session de débogage (SDM) est appelé en choisissant le **déboguer** menu, puis en choisissant **Démarrer**. Pour plus d’informations, consultez [lancer un programme](../../extensibility/debugger/launching-a-program.md).

2.  Les appels SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode).

3.  Selon le modèle de processus de moteur (dé) de débogage, le `IDebugProgramNodeAttach2::OnAttach` méthode retourne une des méthodes suivantes, qui détermine ce qui se passe ensuite.

     Si `S_FALSE` retourne, le moteur de débogage (dé) doit être chargé en cours de la machine virtuelle.

     ou

     Si `S_OK` retourne, le DE doit être chargé dans le processus du SDM. Le SDM effectue ensuite les tâches suivantes :

    1.  Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de l’Allemagne.

    2.  Crée l’Allemagne.

    3.  Appels [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md).

4.  L’envoie DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

5.  L’envoie DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

6.  L’envoie DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

7.  L’envoie DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

8.  L’envoie DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

## <a name="see-also"></a>Voir aussi
- [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)