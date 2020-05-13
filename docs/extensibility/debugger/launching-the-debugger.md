---
title: Lancement du Debugger (fr) Microsoft Docs
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
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738446"
---
# <a name="launch-the-debugger"></a>Lancer le débbugger
Lancer le débbugger nécessite d’envoyer la séquence correcte de méthodes et d’événements avec leurs attributs appropriés.

## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et d’événements

1. Le gestionnaire de déboçon de session (SDM) est appelé en choisissant le menu **Debug,** puis en choisissant **Start**. Pour plus d’informations, voir [Lancer un programme](../../extensibility/debugger/launching-a-program.md).

2. Le SDM appelle la méthode [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. Basé sur le modèle de processus du `IDebugProgramNodeAttach2::OnAttach` moteur de débogé (DE), la méthode renvoie l’une des méthodes suivantes, qui détermine ce qui se passe ensuite.

     Si `S_FALSE` le retour, le moteur de débogé (DE) doit être chargé dans le processus de la machine virtuelle.

     -ou-

     Si `S_OK` le DE doit être chargé en cours de traitement du SDM. Le SDM effectue ensuite les tâches suivantes :

    1. Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de la DE.

    2. Co-crée le DE.

    3. Appels [Joindre](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Le DE envoie un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au `EVENT_SYNC` SDM avec un attribut.

5. Le DE envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au `EVENT_SYNC` SDM avec un attribut.

6. Le DE envoie un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au `EVENT_SYNC` SDM avec un attribut.

7. Le DE envoie un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au `EVENT_SYNC` SDM avec un attribut.

8. Le DE envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au `EVENT_SYNC` SDM avec un attribut.

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
