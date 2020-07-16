---
title: Contrôle de l’exécution | Microsoft Docs
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
ms.openlocfilehash: 9c59831efb2fc97ad1bb2891fd93a67fe79f8eff
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387003"
---
# <a name="control-of-execution"></a>Contrôle de l’exécution
Le moteur de débogage (DE) envoie généralement l’un des événements suivants comme dernier événement de démarrage :

- Événement de point d’entrée, s’il est attaché à un programme récemment lancé

- L’événement de fin de chargement, s’il est attaché à un programme qui est déjà en cours d’exécution

  Ces deux événements arrêtent les événements, ce qui signifie que le DE attend une réponse de l’utilisateur au moyen de l’IDE. Pour plus d’informations, consultez [modes opérationnels](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Événement d’arrêt
 Quand un événement d’arrêt est envoyé à la session de débogage :

1. Le programme et le thread qui contiennent le pointeur d’instruction actuel peuvent être obtenus à partir de l’interface d’événement.

2. L’IDE détermine le fichier et la position actuels du code source, qu’il affiche en surbrillance dans l’éditeur.

3. La session de débogage répond généralement à ce premier événement d’arrêt en appelant la méthode **continue** du programme.

4. Le programme s’exécute alors jusqu’à ce qu’il rencontre une condition d’arrêt, telle que l’atteinte d’un point d’arrêt. Dans ce cas, le DE envoie un événement de point d’arrêt à la session de débogage. L’événement DE point d’arrêt est un événement d’arrêt, et le DE nouveau attend une réponse de l’utilisateur.

5. Si l’utilisateur choisit d’effectuer un pas à pas détaillé, au-dessus ou à l’extérieur d’une fonction, l’IDE invite la session de débogage à appeler la méthode du programme `Step` . L’IDE passe ensuite l’unité de l’étape (instruction, instruction ou ligne) et le type d’étape (s’il faut effectuer un pas à pas détaillé, au-dessus ou à l’extérieur de la fonction). Lorsque l’étape est terminée, le DE envoie un événement étape terminer à la session de débogage, qui est un événement d’arrêt.

    -ou-

    Si l’utilisateur choisit de continuer l’exécution à partir du pointeur d’instruction actuel, l’IDE invite la session de débogage à appeler la méthode **Execute** du programme. Le programme reprend l’exécution jusqu’à ce qu’il rencontre la prochaine condition d’arrêt.

    -ou-

    Si la session de débogage doit ignorer un événement d’arrêt particulier, la session de débogage appelle la méthode **continue** du programme. Si le programme a effectué un pas à pas détaillé, dépassé ou sortant d’une fonction lorsqu’il a rencontré la condition d’arrêt, il continue l’étape.

   Par programmation, lorsque la méthode DE rencontre une condition d’arrêt, elle envoie les événements d’arrêt en tant que [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au gestionnaire de débogage de session (SDM) au moyen d’une interface [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Le DE passe les interfaces [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) et [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) qui représentent le programme et le thread contenant le pointeur d’instruction actuel. Le SDM appelle [IDebugThread2 :: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour récupérer le frame de pile supérieur et appelle [IDebugStackFrame2 :: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour récupérer le contexte de document associé au pointeur d’instruction actuel. Ce contexte de document est généralement un nom de fichier de code source, une ligne et un numéro de colonne. L’IDE les utilise pour mettre en surbrillance le code source qui contient le pointeur d’instruction en cours.

   Le SDM répond généralement à ce premier événement d’arrêt en appelant [IDebugProgram2 :: continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Le programme s’exécute alors jusqu’à ce qu’il rencontre une condition d’arrêt, telle que l’atteinte d’un point d’arrêt, auquel cas le service DE envoie une [interface IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) au SDM. L’événement DE point d’arrêt est un événement d’arrêt, et le DE nouveau attend une réponse de l’utilisateur.

   Si l’utilisateur choisit d’effectuer un pas à pas détaillé, au-dessus ou à l’extérieur d’une fonction, l’IDE invite le SDM à appeler [IDebugProgram2 :: Step](../../extensibility/debugger/reference/idebugprogram2-step.md). L’IDE transmet ensuite le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instruction, instruction ou Line) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md), c’est-à-dire, s’il faut effectuer un pas à pas détaillé, au-dessus ou à l’extérieur de la fonction. Lorsque l’étape est terminée, le DE envoie une interface [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) au SDM, qui est un événement d’arrêt.

   Si l’utilisateur choisit de continuer l’exécution à partir du pointeur d’instruction actuel, l’IDE demande au SDM d’appeler [IDebugProgram2 :: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Le programme reprend l’exécution jusqu’à ce qu’il rencontre la prochaine condition d’arrêt.

   Si le package de débogage est destiné à ignorer un événement d’arrêt particulier, le package de débogage appelle le SDM, qui appelle [IDebugProgram2 :: continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si le programme a été pas à pas détaillé, dépassé ou en dehors d’une fonction lorsqu’il a rencontré la condition d’arrêt, il continue l’étape. Cela implique que le programme gère un état d’exécution pas à pas, afin qu’il sache comment continuer.

   Les appels effectués par le SDM à `Step` , **s’exécutent**et se **poursuivent** sont asynchrones, ce qui signifie que le SDM s’attend à ce que l’appel soit retourné rapidement. Si le DE envoie un événement d’arrêt SDM sur le même thread avant `Step` , **Execute**ou **continue** retourne, le SDM cesse de répondre.

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
