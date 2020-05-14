---
title: Attachement et détachement à un programme Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739270"
---
# <a name="attaching-and-detaching-to-a-program"></a>Attachement et détachement à un programme
L’attachement du débbuggeur nécessite l’envoi de la séquence correcte de méthodes et d’événements avec les attributs appropriés.

## <a name="sequence-of-methods-and-events"></a>Séquence de méthodes et d’événements

1. Le gestionnaire de débogé de session (SDM) appelle la méthode [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    Basé sur le modèle de processus du `IDebugProgramNodeAttach2::OnAttach` moteur de débogé (DE), la méthode renvoie l’une des méthodes suivantes, qui détermine ce qui se passe ensuite.

    Si `S_FALSE` elle est retournée, le moteur de débogé a été fixé avec succès au programme. Dans le cas contraire, la méthode [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée pour compléter le processus d’attachement.

    Si `S_OK` elle est retournée, le DE doit être chargé dans le même processus que le SDM. Le SDM effectue les tâches suivantes :

   1. Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de la DE.

   2. Co-crée le DE.

   3. Appels [Joindre](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Le DE envoie un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au `EVENT_SYNC` SDM avec un attribut.

3. Le DE envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au `EVENT_SYNC` SDM avec un attribut.

4. Le DE envoie un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au `EVENT_SYNC_STOP` SDM avec un attribut.

   Le détachement d’un programme est un processus simple en deux étapes, comme suit :

5. Le SDM appelle [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Le DE envoie un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)
