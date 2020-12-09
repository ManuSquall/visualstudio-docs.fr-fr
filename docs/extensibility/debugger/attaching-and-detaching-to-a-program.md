---
title: Attachement et détachement d’un programme | Microsoft Docs
description: En savoir plus sur l’envoi de la séquence correcte des méthodes et des événements avec les attributs appropriés pour l’attachement d’un débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b71a78dcee62f89dee4c54b53c1026f42895793
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913787"
---
# <a name="attaching-and-detaching-to-a-program"></a>Attachement et détachement d’un programme
L’attachement du débogueur nécessite l’envoi de la séquence correcte des méthodes et des événements avec les attributs appropriés.

## <a name="sequence-of-methods-and-events"></a>Séquence de méthodes et d’événements

1. Le gestionnaire de débogage de session (SDM) appelle la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

    Selon le modèle DE processus du moteur DE débogage (DE), la `IDebugProgramNodeAttach2::OnAttach` méthode retourne l’une des méthodes suivantes, qui détermine ce qui se passe ensuite.

    Si `S_FALSE` est retourné, le moteur de débogage a été attaché au programme. Sinon, la méthode d' [attachement](../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée pour terminer le processus d’attachement.

    Si `S_OK` est retourné, le de doit être chargé dans le même processus que le SDM. Le SDM effectue les tâches suivantes :

   1. Appelle [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour récupérer les informations du moteur de.

   2. Co-crée le DE.

   3. Appelle [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Le DE envoie un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.

3. Le DE envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.

4. Le DE envoie un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM avec un `EVENT_SYNC_STOP` attribut.

   Le détachement d’un programme est un processus simple en deux étapes, comme suit :

5. Le SDM appelle [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Le DE envoie un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
