---
title: Attachement direct à un programme | Microsoft Docs
description: Découvrez comment Visual Studio implémente l’attachement d’un moteur de débogage à un processus qui est déjà en cours d’exécution à l’aide de cette procédure dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80ee40d60b5a7511c3f44c22c16e02751d9f1f36
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913774"
---
# <a name="attach-directly-to-a-program"></a>Attachement direct à un programme
Les utilisateurs qui souhaitent déboguer des programmes dans un processus qui est déjà en cours d’exécution suivent ce processus :

1. Dans l’IDE, choisissez la commande **déboguer les processus** dans le menu **Outils** .

    La boîte de dialogue **Processus** s’affiche.

2. Choisissez un processus et cliquez sur le bouton **attacher** .

    La boîte **de dialogue Attacher au processus** s’affiche avec la liste de tous les moteurs de débogage (des) installés sur l’ordinateur.

3. Spécifiez les DEs à utiliser pour déboguer le processus sélectionné, puis cliquez sur **OK**.

   Le package de débogage démarre une session de débogage et transmet la liste des à celle-ci. La session de débogage passe à son tour cette liste, ainsi qu’une fonction de rappel, au processus sélectionné, puis demande au processus d’énumérer ses programmes en cours d’exécution.

   Par programmation, en réponse à la demande de l’utilisateur, le package de débogage instancie le gestionnaire de débogage de session (SDM) et lui transmet la liste des sélectionnés. Avec la liste, le package de débogage passe l’interface [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) du SDM. Le package de débogage transmet la liste des des au processus sélectionné en appelant [IDebugProcess2 :: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Le SDM appelle ensuite [IDebugProcess2 :: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sur le port pour énumérer les programmes en cours d’exécution dans le processus.

   À partir de ce point, chaque moteur de débogage est attaché à un programme exactement comme détaillé dans [attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md), à deux exceptions près.

   Pour plus d’efficacité, les DEs, qui sont implémentés pour partager un espace d’adressage avec le SDM, sont regroupés afin que chaque DE ait un ensemble de programmes auquel il sera attaché. Dans ce cas, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) appelle [IDebugEngine2 :: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) et lui passe un tableau de programmes à attacher.

   La deuxième exception est que les événements DE démarrage envoyés par un DE l’attachement à un programme qui est déjà en cours d’exécution n’incluent généralement pas l’événement DE point d’entrée.

## <a name="see-also"></a>Voir aussi
- [Envoi d’événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
