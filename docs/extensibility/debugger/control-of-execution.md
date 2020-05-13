---
title: Contrôle de l’exécution (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739075"
---
# <a name="control-of-execution"></a>Contrôle de l’exécution
Le moteur de débogé (DE) envoie généralement l’un des événements suivants comme le dernier événement de démarrage:

- L’événement du point d’entrée, s’il s’attache à un programme nouvellement lancé

- L’événement complet de charge, s’il s’attache à un programme qui est déjà en cours d’exécution

  Ces deux événements sont l’arrêt des événements, ce qui signifie que le DE attend une réponse de l’utilisateur au moyen de l’IDE. Pour plus d’informations, voir [modes opérationnels](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Arrêt de l’événement
 Lorsqu’un événement d’arrêt est envoyé à la session de débog :

1. Le programme et le fil qui contiennent le pointeur d’instruction actuel peuvent être obtenus à partir de l’interface de l’événement.

2. L’IDE détermine le fichier et la position actuels du code source, qu’il affiche comme indiqué dans l’éditeur.

3. La séance de débog répond généralement à ce premier événement d’arrêt en appelant la méthode **Continuer** du programme.

4. Le programme fonctionne ensuite jusqu’à ce qu’il rencontre une condition d’arrêt, comme frapper un point d’arrêt. Dans ce cas, le DE envoie un événement de point d’arrêt à la session de débogé. L’événement de point d’arrêt est un événement d’arrêt, et le DE attend à nouveau une réponse de l’utilisateur.

5. Si l’utilisateur choisit d’entrer, de plus ou de sortir d’une fonction, l’IDE invite la session de débogé à appeler la méthode du `Step` programme. L’IDE passe ensuite l’unité d’étape (instruction, déclaration ou ligne) et le type d’étape (que ce soit pour entrer, plus ou hors de la fonction). Lorsque l’étape est terminée, le DE envoie un événement complet étape à la session de débog, qui est un événement d’arrêt.

    -ou-

    Si l’utilisateur choisit de continuer à exécuter à partir du pointeur d’instruction actuel, l’IDE invite la session de débog à appeler la méthode **Exécuter** du programme. Le programme reprend l’exécution jusqu’à ce qu’il rencontre la condition d’arrêt suivante.

    -ou-

    Si la session de débog doit ignorer un événement d’arrêt particulier, la session de débaille appelle la méthode **Continuer** du programme. Si le programme entre, plus ou hors d’une fonction lorsqu’il a rencontré l’état d’arrêt, il continue l’étape.

   Programmatiquement, lorsque le DE rencontre une condition d’arrêt, il envoie des événements d’arrêt tels que [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au gestionnaire de débbug session (SDM) au moyen d’une interface [IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Le DE passe les interfaces [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) et [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) qui représentent le programme et le thread contenant le pointeur d’instruction actuel. Le SDM appelle [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir le cadre de pile supérieure et appelle [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir le contexte de document associé au pointeur d’instruction actuel. Ce contexte de document est généralement un nom de fichier de code source, une ligne et un numéro de colonne. L’IDE les utilise pour mettre en évidence le code source qui contient le pointeur d’instruction actuel.

   Le SDM répond généralement à ce premier événement d’arrêt en appelant [IDebugProgram2:Continuer](../../extensibility/debugger/reference/idebugprogram2-continue.md). Le programme fonctionne ensuite jusqu’à ce qu’il rencontre une condition d’arrêt, comme frapper un point d’arrêt, auquel cas le DE envoie une [interface IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) à la SDM. L’événement de point d’arrêt est un événement d’arrêt, et le DE attend à nouveau une réponse de l’utilisateur.

   Si l’utilisateur choisit d’entrer dans, plus ou hors d’une fonction, l’IDE invite le SDM à appeler [IDebugProgram2:Step](../../extensibility/debugger/reference/idebugprogram2-step.md). L’IDE passe ensuite le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instruction, déclaration ou ligne) et le [STEPKIND](../../extensibility/debugger/reference/stepkind.md), c’est-à-dire, que ce soit pour entrer, plus ou hors de la fonction. Lorsque l’étape est terminée, le DE envoie une interface [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) au SDM, qui est un événement d’arrêt.

   Si l’utilisateur choisit de continuer à exécuter à partir du pointeur d’instruction actuel, l’IDE demande au SDM d’appeler [IDebugProgram2:Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Le programme reprend l’exécution jusqu’à ce qu’il rencontre la condition d’arrêt suivante.

   Si le paquet de débog est d’ignorer un événement d’arrêt particulier, le paquet de débog appelle le SDM, qui appelle [IDebugProgram2:Continuer](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si le programme entre, est terminé ou hors d’une fonction lorsqu’il a rencontré l’état d’arrêt, il poursuit l’étape. Cela implique que le programme maintient un état de marche, de sorte qu’il sait comment continuer.

   Les appels que le `Step`SDM fait à , **Exécuter**, et **Continuer** sont asynchrones, ce qui signifie que le SDM s’attend à l’appel de revenir rapidement. Si le DE envoie au SDM un `Step`événement d’arrêt sur le même thread avant, **Exécuter**, ou **Continuer** les retours, le SDM se bloque.

## <a name="see-also"></a>Voir aussi
- [Tâches de débogé](../../extensibility/debugger/debugging-tasks.md)
