---
title: Envoi des événements requis (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712993"
---
# <a name="send-the-required-events"></a>Envoyer les événements requis
Utilisez cette procédure pour l’envoi d’événements requis.

## <a name="process-for-sending-required-events"></a>Processus d’envoi des événements requis
 Les événements suivants sont nécessaires, dans cet ordre, lors de la création d’un moteur de débogé (DE) et de l’attacher à un programme:

1. Envoyez un objet d’événement [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au gestionnaire de débogage de session (SDM) lorsque le DE est paraprimé pour débogage d’un ou plusieurs programmes dans un processus.

2. Lorsque le programme à déboiffer est attaché à, envoyez un objet d’événement [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM. Cet événement peut être un événement d’arrêt, selon la conception de votre moteur.

3. Si le programme est attaché au moment du lancement du processus, envoyez un objet d’événement [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM pour aviser l’IDE du nouveau thread. Cet événement peut être un événement d’arrêt, selon la conception de votre moteur.

4. Envoyer un objet d’événement [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM lorsque le programme en cours de débbugged est terminé de chargement ou lors de l’attachement au programme est terminée. Cet événement doit être un événement d’arrêt.

5. Si l’application à déboguer est lancée, envoyez un objet d’événement [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM lorsque la première instruction de code dans l’architecture de run-time est sur le point d’être exécutée. Cet événement est toujours un événement d’arrêt. Lorsque vous entrez dans la session de débogage, l’IDE s’arrête sur cet événement.

> [!NOTE]
> De nombreuses langues utilisent des initialisateurs globaux ou des fonctions externes précompilées (de la bibliothèque ou de la _Main de la CRT) au début de leur code. Si la langue du programme que vous débogage contient l’un de ces types d’éléments avant le point d’entrée initial, ce code est exécuté et l’événement du point d’entrée est envoyé lorsque le point d’entrée de l’utilisateur, tel que **principal** ou `WinMain`, est atteint.

## <a name="see-also"></a>Voir aussi
- [Permettre la déboiffation d’un programme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
