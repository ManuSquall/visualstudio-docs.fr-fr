---
title: "Contrôle de l’exécution | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79d888e9b50d18b4a9d46a8914381db27f09698d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="control-of-execution"></a>Contrôle de l’exécution
Le moteur de débogage (DE) envoie généralement un des événements suivants en tant que le dernier événement de démarrage :  
  
-   L’événement de point d’entrée, si l’attachement à un programme lancé récemment  
  
-   L’événement complete charge, si l’attachement à un programme qui est déjà en cours d’exécution  
  
 Ces deux événements sont événements d’arrêt, c'est-à-dire que le D’attend une réponse de l’utilisateur au moyen de l’IDE. Pour plus d’informations, consultez [Modes opérationnels](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Événement d’arrêt  
 Quand un événement d’arrêt est envoyé à la session de débogage :  
  
1.  Le programme et le thread qui contiennent le pointeur d’instruction en cours peuvent être obtenus à partir de l’interface d’événement.  
  
2.  L’IDE détermine le fichier de code source en cours et de la position, qu’elle affiche en surbrillance dans l’éditeur.  
  
3.  La session de débogage répond généralement à ce premier événement d’arrêt en appelant du programme **continuer** (méthode).  
  
4.  Ensuite, le programme s’exécute jusqu'à ce qu’il rencontre une condition d’arrêt, telles que l’atteinte d’un point d’arrêt, dans lequel cas le DE envoie un événement de point d’arrêt à la session de débogage. L’événement de point d’arrêt est un événement d’arrêt et la DE nouveau attend une réponse de l’utilisateur.  
  
5.  Si l’utilisateur choisit de pas à pas détaillé, plus ou en dehors d’une fonction, l’IDE vous invite à entrer la session de débogage pour appeler le programme `Step` méthode, en lui passant l’unité d’étape (instruction, l’instruction ou ligne) et le type d’étape : autrement dit, s’il faut pas à pas détaillé, plus , ou en dehors de la fonction. Lorsque l’étape est terminée, le D’envoie un événement complete étape à la session de débogage, qui est un événement d’arrêt.  
  
     ou  
  
     Si l’utilisateur choisit de continuer l’exécution à partir du pointeur d’instruction en cours, l’IDE vous invite à entrer la session de débogage pour appeler le programme **Execute** (méthode). Le programme reprend l’exécution jusqu'à ce qu’il rencontre la condition d’arrêt suivante.  
  
     ou  
  
     Si la session de débogage est pour ignorer un événement d’arrêt particulier, la session de débogage appelle du programme **continuer** (méthode). Si le programme a été pas à pas détaillé, principal ou en dehors d’une fonction lorsqu’il a rencontré la condition d’arrêt, il continue de l’étape.  
  
 Par programme, lorsque le DE rencontre une condition d’arrêt, il envoie des événements d’arrêt, tels que [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) pour le Gestionnaire de session de débogage (SDM) à l’aide de un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. Les étapes DE la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) et [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces qui représentent le programme et le thread qui contient le pointeur d’instruction en cours. Les appels SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir le frame de pile supérieur et les appels [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir le contexte de document associé à l’instruction en cours pointeur. Ce contexte de document est généralement une source code nom, ligne et colonne numéro de fichier. L’IDE utilise pour mettre en surbrillance le code source qui contient le pointeur d’instruction en cours.  
  
 Le SDM répond généralement à ce premier événement d’arrêt en appelant [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Le programme s’exécute puis jusqu'à ce qu’il rencontre une condition d’arrêt, telles que l’atteinte d’un point d’arrêt, dans lequel cas le DE envoie un [IDebugBreakpointEvent2 Interface](../../extensibility/debugger/reference/idebugbreakpointevent2.md) pour le SDM. L’événement de point d’arrêt est un événement d’arrêt et la DE nouveau attend une réponse de l’utilisateur.  
  
 Si l’utilisateur choisit de pas à pas détaillé, plus ou en dehors d’une fonction, l’IDE vous invite à entrer le SDM pour appeler [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), en lui passant le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instruction, l’instruction ou ligne) et le [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), autrement dit, s’il faut pas à pas détaillé, principal ou en dehors de la fonction. Lorsque l’étape est terminée, le D’envoie un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface SDM, ce qui est un événement d’arrêt.  
  
 Si l’utilisateur choisit de continuer l’exécution à partir du pointeur d’instruction en cours, l’IDE vous demande le SDM pour appeler [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Le programme reprend l’exécution jusqu'à ce qu’il rencontre la condition d’arrêt suivante.  
  
 Si le package de débogage est pour ignorer un événement d’arrêt particulier, le package de débogage appelle le SDM, qui appelle [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si le programme a été pas à pas détaillé, principal ou en dehors d’une fonction lorsqu’il a rencontré la condition d’arrêt, il continue de l’étape. Cela implique que le programme conserve un état d’exécution pas à pas, de sorte qu’il sache comment continuer.  
  
 Les appels à la SDM `Step`, **Execute**, et **continuer** sont asynchrone, ce qui signifie que le SDM attend l’appel doit retourner rapidement. Si le D’envoie le SDM un événement d’arrêt sur le même thread avant `Step`, **Execute**, ou **continuer** retourne, le SDM se bloque.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)