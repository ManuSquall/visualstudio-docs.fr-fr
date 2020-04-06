---
title: Notifier le port (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738319"
---
# <a name="notify-the-port"></a>Aviser le port
Après le lancement d’un programme, le port doit être avisé, comme suit :

1. Lorsqu’un port reçoit un nouveau nœud de programme, il renvoie un événement de création de programme à la session de débogé. L’événement porte avec lui une interface qui représente le programme.

2. La session de débogé demande le programme pour l’identification d’un moteur de débogé (DE) qui peut s’attacher à.

3. La session de déboptille vérifie si le DE est sur la liste des DE admissibles pour ce programme. La session de débog obtient cette liste à partir des paramètres de programme actif de la solution, à l’origine passé à elle par le paquet de débogé.

    Le DE doit être sur la liste admissible, sinon le DE ne sera pas attaché au programme.

   Sur le plan programmatique, lorsqu’un port reçoit pour la première fois un nouveau nœud de programme, il crée une interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) pour représenter le programme.

> [!NOTE]
> Cela ne doit pas `IDebugProgram2` être confondu avec l’interface créée plus tard par le moteur de débogé (DE).

 Le port envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement de création du programme de retour au `IConnectionPoint` gestionnaire de déboissement de session (SDM) au moyen d’une interface COM.

> [!NOTE]
> Cela ne doit pas `IDebugProgramCreateEvent2` être confondu avec l’interface, qui est envoyé plus tard par le DE.

 Avec l’interface d’événement elle-même, le port envoie [l’IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), et [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces, qui représentent le port, le processus, et le programme, respectivement. Le SDM appelle [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour obtenir le GUID de la DE qui peut déboiffer le programme. Le GUID a été obtenu à l’origine à partir de l’interface [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 Le SDM vérifie si le DE est sur la liste des DE admissibles. Le SDM obtient cette liste à partir des paramètres de programme actifs de la solution, initialement transmis par le paquet de débogé. Le DE doit être sur la liste admissible, sinon il ne sera pas attaché au programme.

 Une fois que l’identité du DE est connue, le SDM est prêt à l’attacher au programme.

## <a name="see-also"></a>Voir aussi
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
- [Fixation après un lancement](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
