---
title: S’attacher directement à un programme Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739263"
---
# <a name="attach-directly-to-a-program"></a>Joindre directement à un programme
Les utilisateurs qui veulent déboguer les programmes dans un processus qui est déjà en cours d’exécution suivent généralement ce processus:

1. Dans l’IDE, choisissez la commande **Debug Processes** dans le menu **Tools.**

    La boîte de dialogue **Processus** s’affiche.

2. Choisissez un processus et cliquez sur le bouton **Joindre.**

    La boîte de dialogue **Attach to Process** apparaît, énumérant tous les moteurs de débogs (DEs) installés sur la machine.

3. Spécifier les DE à utiliser pour déboiffer le processus sélectionné, puis cliquez **sur OK**.

   Le paquet de débog commence une session de débogé et passe la liste des DE à elle. La session de déboguer à son tour passe cette liste, avec une fonction de rappel, au processus sélectionné, puis demande au processus d’énumérer ses programmes en cours d’exécution.

   Programmatiquement, en réponse à la demande de l’utilisateur, le paquet de débog instantanément le gestionnaire de débopathie de session (SDM) et passe la liste des DE sélectionnés à elle. Avec la liste, le paquet de débogé passe le SDM une interface [IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Le paquet de débog passe la liste des DE au processus sélectionné en appelant [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Le SDM appelle ensuite [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sur le port pour énumérer les programmes en cours d’exécution dans le processus.

   A partir de ce moment, chaque moteur de débogé est fixé à un programme exactement aussi détaillé dans [Attaching après un lancement](../../extensibility/debugger/attaching-after-a-launch.md), à deux exceptions près.

   Pour plus d’efficacité, les DE qui sont mis en œuvre pour partager un espace d’adresse avec le SDM sont regroupés de sorte que chaque DE dispose d’un ensemble de programmes auxquels il s’attachera. Dans ce cas, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) appelle [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) et passe un éventail de programmes à attacher.

   La deuxième exception est que les événements de démarrage envoyés par un DE attachant à un programme qui est déjà en cours d’exécution n’incluent généralement pas l’événement point d’entrée.

## <a name="see-also"></a>Voir aussi
- [Envoi d’événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
