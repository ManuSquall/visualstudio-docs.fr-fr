---
title: Envoi des événements requis | Microsoft Docs
description: En savoir plus sur les événements ordonnés qui sont requis lors de la création d’un moteur de débogage et de son attachement à un programme dans le débogage Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b04ca7ed68b975bc68fa509cdc75dc507b9603d6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902265"
---
# <a name="send-the-required-events"></a>Envoyer les événements requis
Utilisez cette procédure pour envoyer les événements requis.

## <a name="process-for-sending-required-events"></a>Processus d’envoi des événements requis
 Les événements suivants sont requis, dans cet ordre, lors de la création d’un moteur de débogage (DE) et de son attachement à un programme :

1. Envoie un objet événement [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au gestionnaire de débogage de session (SDM) quand le de est initialisé pour déboguer un ou plusieurs programmes dans un processus.

2. Lorsque le programme à déboguer est attaché à, envoyez un objet d’événement [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM. Il peut s’agir d’un événement d’arrêt, en fonction de la conception de votre moteur.

3. Si le programme est attaché à lorsque le processus est lancé, envoyer un objet d’événement [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM pour notifier l’IDE du nouveau thread. Il peut s’agir d’un événement d’arrêt, en fonction de la conception de votre moteur.

4. Envoie un objet événement [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM lorsque le programme en cours de débogage a fini de se charger ou lorsque l’attachement au programme est terminé. Cet événement doit être un événement d’arrêt.

5. Si l’application à déboguer est lancée, envoyez un objet d’événement [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM lorsque la première instruction de code dans l’architecture Runtime est sur le point d’être exécutée. Cet événement est toujours un événement d’arrêt. Lorsque vous effectuez un pas à pas détaillé dans la session de débogage, l’IDE s’arrête sur cet événement.

> [!NOTE]
> De nombreux langages utilisent des initialiseurs globaux ou des fonctions externes, précompilées (à partir de la bibliothèque CRT ou _Main) au début de leur code. Si la langue du programme que vous déboguez contient l’un de ces types d’éléments avant le point d’entrée initial, ce code est exécuté et l’événement de point d’entrée est envoyé lorsque le point d’entrée de l’utilisateur, tel que **main** ou `WinMain` , est atteint.

## <a name="see-also"></a>Voir aussi
- [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
