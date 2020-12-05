---
title: Lancement du débogueur | Microsoft Docs
description: En savoir plus sur la séquence des méthodes et des événements avec leurs attributs appropriés nécessaires au lancement du débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40b91ae695a5e78745c01c5ac974411ac924f8f0
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606656"
---
# <a name="launch-the-debugger"></a>Lancez le débogueur
Le lancement du débogueur nécessite l’envoi de la séquence correcte des méthodes et des événements avec leurs attributs appropriés.

## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et d’événements

1. Le gestionnaire de débogage de session (SDM) est appelé en choisissant le menu **Déboguer** , puis en sélectionnant **Démarrer**. Pour plus d’informations, consultez [lancer un programme](../../extensibility/debugger/launching-a-program.md).

2. Le SDM appelle la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

3. Selon le modèle DE processus du moteur DE débogage (DE), la `IDebugProgramNodeAttach2::OnAttach` méthode retourne l’une des méthodes suivantes, qui détermine ce qui se passe ensuite.

     Si `S_FALSE` retourne, le moteur de débogage doit être chargé dans le processus de l’ordinateur virtuel.

     -ou-

     Si `S_OK` retourne, le de doit être chargé dans le processus du SDM. Le SDM effectue ensuite les tâches suivantes :

    1. Appelle [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour récupérer les informations du moteur de.

    2. Co-crée le DE.

    3. Appelle [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Le DE envoie un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.

5. Le DE envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.

6. Le DE envoie un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.

7. Le DE envoie un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM avec un `EVENT_SYNC` attribut.

8. Le DE envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM avec un `EVENT_SYNC` attribut.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
