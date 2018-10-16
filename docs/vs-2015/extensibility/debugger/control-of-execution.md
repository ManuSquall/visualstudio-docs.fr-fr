---
title: Contrôle de l’exécution | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31584a0f59369def8a1a89ad2544b94ef9633366
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302378"
---
# <a name="control-of-execution"></a>Contrôle de l’exécution
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le moteur de débogage (dé) envoie généralement un des événements suivants en tant que le dernier événement de démarrage :  
  
-   L’événement de point d’entrée, si l’attachement à un programme lancé récemment  
  
-   L’événement complete charge, si l’attachement à un programme qui est déjà en cours d’exécution  
  
 Ces deux événements sont événements d’arrêt, ce qui signifie que l’Allemagne attend une réponse de l’utilisateur au moyen de l’IDE. Pour plus d’informations, consultez [les Modes de fonctionnement](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Arrêt de l’événement  
 Quand un événement d’arrêt est envoyé à la session de débogage :  
  
1.  Le programme et le thread qui contiennent le pointeur d’instruction en cours peuvent être obtenus à partir de l’interface d’événement.  
  
2.  L’IDE détermine le fichier de code source en cours et de la position, qui s’affiche en surbrillance dans l’éditeur.  
  
3.  La session de débogage répond généralement à ce premier événement d’arrêt en appelant le programme **continuer** (méthode).  
  
4.  Ensuite, le programme s’exécute jusqu'à ce qu’il rencontre une condition d’arrêt, comme atteindre un point d’arrêt, dans lequel cas le DE envoie un événement de point d’arrêt à la session de débogage. L’événement de point d’arrêt est un événement d’arrêt et l’Allemagne attend de nouveau une réponse de l’utilisateur.  
  
5.  Si l’utilisateur choisit de pas à pas détaillé, plus ou en dehors d’une fonction, l’IDE vous invite à entrer la session de débogage pour appeler le programme `Step` méthode, en lui passant l’unité d’étape (instruction, instruction ou ligne) et le type d’étape : autrement dit, s’il faut pas à pas détaillé, plus , ou en dehors de la fonction. Lorsque l’étape est terminée, le D’envoie un événement de fin d’étape à la session de débogage, qui est un événement d’arrêt.  
  
     - ou -  
  
     Si l’utilisateur choisit de continuer à s’exécuter à partir du pointeur d’instruction en cours, l’IDE vous invite à entrer la session de débogage pour appeler le programme **Execute** (méthode). Le programme reprend son exécution jusqu'à ce qu’il rencontre la condition d’arrêt suivante.  
  
     - ou -  
  
     Si la session de débogage consiste à ignorer un événement d’arrêt particulier, la session de débogage appelle le programme **continuer** (méthode). Si le programme a été pas à pas détaillé dans, au-dessus ou en dehors d’une fonction lorsqu’il a rencontré la condition d’arrêt, puis il continue l’étape.  
  
 Par programme, lors de la DE rencontre une condition d’arrêt, il envoie des événements d’arrêt, tels que [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) avec le Gestionnaire de débogage de session (SDM) par le biais de un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. Le passe DE la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) et [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces qui représentent le programme et le thread qui contient le pointeur d’instruction en cours. Les appels SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir le frame de pile supérieur et les appels [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir le contexte de document associé à l’instruction actuelle pointeur. Ce contexte de document est généralement un fichier de code source qu’un nombre nom, ligne et colonne. L’IDE utilise pour mettre en surbrillance le code source qui contient le pointeur d’instruction en cours.  
  
 Le SDM répond généralement à ce premier événement d’arrêt en appelant [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Le programme s’exécute puis jusqu'à ce qu’il rencontre une condition d’arrêt, comme atteindre un point d’arrêt, dans lequel cas le DE envoie un [IDebugBreakpointEvent2 Interface](../../extensibility/debugger/reference/idebugbreakpointevent2.md) pour le SDM. L’événement de point d’arrêt est un événement d’arrêt et l’Allemagne attend de nouveau une réponse de l’utilisateur.  
  
 Si l’utilisateur choisit de pas à pas détaillé, plus ou en dehors d’une fonction, l’IDE vous invite à entrer le SDM pour appeler [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), en lui passant le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instruction, instruction ou ligne) et le [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), autrement dit, s’il faut passer dans, sur ou en dehors de la fonction. Lorsque l’étape est terminée, l’Allemagne envoie un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface pour le SDM, qui est un événement d’arrêt.  
  
 Si l’utilisateur choisit de continuer à s’exécuter à partir du pointeur d’instruction en cours, l’IDE vous demande le SDM pour appeler [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Le programme reprend son exécution jusqu'à ce qu’il rencontre la condition d’arrêt suivante.  
  
 Si le package de débogage consiste à ignorer un événement d’arrêt particulier, le package de débogage appelle le SDM, qui appelle [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si le programme a été pas à pas détaillé dans, au-dessus ou en dehors d’une fonction lorsqu’il a rencontré la condition d’arrêt, puis il continue l’étape. Cela implique que le programme maintient un état d’exécution pas à pas, afin qu’il sache comment continuer.  
  
 Les appels au SDM `Step`, **Execute**, et **continuer** sont asynchrone, ce qui signifie que le SDM attend l’appel doit retourner rapidement. Si le D’envoie le SDM un événement d’arrêt sur le même thread avant `Step`, **Execute**, ou **continuer** retourne, le SDM se bloque.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)

