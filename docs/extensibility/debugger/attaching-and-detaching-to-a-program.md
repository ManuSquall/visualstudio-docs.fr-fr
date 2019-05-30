---
title: Attachement et détachement d’un programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edbabb078bc46c55431276e9c1fe8d1f807d76f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350909"
---
# <a name="attaching-and-detaching-to-a-program"></a>Attachement et détachement d’un programme
Attacher le débogueur nécessite l’envoi de la séquence des méthodes et des événements avec les attributs corrects.

## <a name="sequence-of-methods-and-events"></a>Séquence de méthodes et événements

1. Le Gestionnaire de session de débogage (SDM) appelle le [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode).

    Selon le modèle de processus de moteur (dé) de débogage, le `IDebugProgramNodeAttach2::OnAttach` méthode retourne une des méthodes suivantes, qui détermine ce qui se passe ensuite.

    Si `S_FALSE` est retourné, le moteur de débogage a correctement été attaché au programme. Sinon, le [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée pour terminer le processus d’attachement.

    Si `S_OK` est retourné, l’Allemagne est chargé dans le même processus que le SDM. Le SDM effectue les tâches suivantes :

   1. Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de l’Allemagne.

   2. Crée l’Allemagne.

   3. Appels [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. L’envoie DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

3. L’envoie DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.

4. L’envoie DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) pour le SDM avec un `EVENT_SYNC_STOP` attribut.

   Le détachement d’un programme est un simple, un processus en deux étapes, comme suit :

5. Les appels SDM [détachement](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. L’envoie DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Voir aussi
- [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)