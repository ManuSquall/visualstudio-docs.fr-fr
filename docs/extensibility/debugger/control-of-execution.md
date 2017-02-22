---
title: "Contr&#244;le de l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], contrôle d'exécution"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Contr&#244;le de l&#39;ex&#233;cution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie en général un des événements suivants comme dernier événement startup :  
  
-   L'événement de point d'entrée, si l'attachement à un programme récemment lancé  
  
-   L'événement terminé de charge, si l'attachement à un programme en cours de exécution  
  
 Ces deux événements cesse d'événements, ce qui signifie que le De attend une réponse de l'utilisateur au moyen de l'IDE.  Pour plus d'informations, consultez [modes opérationnels](../../extensibility/debugger/operational-modes.md).  
  
## Arrêter l'événement  
 Lorsqu'un événement arrêtant est envoyé à la session de débogage :  
  
1.  le programme et le thread qui contiennent le pointeur d'instruction actuel peuvent être obtenus à partir de l'interface d'événement.  
  
2.  L'IDE détermine le fichier de code source et la position actuelle, qu'elle affiche en surbrillance dans l'éditeur.  
  
3.  La session de débogage répond généralement à ce premier événement arrêtant en appelant la méthode de **Continuer** du programme.  
  
4.  Le programme s'exécute alors jusqu'à ce qu'il rencontre une condition cessante, telle que l'accès un point d'arrêt, auquel cas le De envoie un événement point d'arrêt à la session de débogage.  L'événement de point d'arrêt est un événement arrêtant, et De attend à nouveau les réponses d'utilisateur.  
  
5.  Si l'utilisateur choisit d'exécuter pas \- à \- pas, sur, ou à partir d'une fonction, l'IDE invite la session de débogage à appeler la méthode d' `Step` du programme, en lui passant l'unité de l'étape \(instruction, instruction, ou ligne\) et le type de étape\-qu'est, si exécuter pas \- à \- pas, sur, ou hors de la fonction.  Lorsque l'étape est terminée, le De envoie un événement complet d'étape à la session de débogage, qui est un événement arrêtant.  
  
     ou  
  
     Si l'utilisateur choisit de poursuivre l'exécution du pointeur d'instruction actuel, l'IDE invite la session de débogage à appeler la méthode d' **Exécuter** du programme.  Le programme l'exécution se poursuit jusqu'à ce qu'il rencontre l'état arrêtant suivant.  
  
     ou  
  
     Si la session de débogage doit ignorer un événement arrêtant particulier, la session de débogage appelle la méthode de **Continuer** du programme.  Si le programme faisait pas \- à \- pas, sur, ou à partir d'une fonction lorsqu'il a rencontré la condition cessante, il reprend l'étape.  
  
 Par programme, lorsque le De rencontre une condition cessante, il envoie les événements cessants de sorte qu' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au gestionnaire de débogage de session \(SDM\) au moyen d'une interface d' [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  Le De passe les interfaces d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) et d' [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) qui représentent le programme et le thread contenant le pointeur d'instruction actuel.  Le SDM appelle [IDebugThread2 : : EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir le frame de pile supérieur et appelle [IDebugStackFrame2 : : GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir le contexte de document associé au pointeur d'instruction actuel.  ce contexte de document est en général un nom de fichier de code source, une ligne, et un numéro de colonne.  L'IDE utilise ces éléments pour mettre en surbrillance le code source qui contient le pointeur d'instruction actuel.  
  
 Le SDM répond généralement à ce premier événement arrêtant en appelant [IDebugProgram2 : : continuez](../../extensibility/debugger/reference/idebugprogram2-continue.md).  Le programme s'exécute alors jusqu'à ce qu'il rencontre une condition cessante, telle que l'accès un point d'arrêt, auquel cas le De envoie [interface IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) au SDM.  L'événement de point d'arrêt est un événement arrêtant, et De attend à nouveau les réponses d'utilisateur.  
  
 Si l'utilisateur choisit d'exécuter pas \- à \- pas, sur, ou à partir d'une fonction, l'IDE invite le SDM à appeler [IDebugProgram2 : : étape](../../extensibility/debugger/reference/idebugprogram2-step.md), en lui passant [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(instruction, instruction, ou ligne\) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md), c. autrement dit., si exécuter pas \- à \- pas, sur, ou hors de la fonction.  Lorsque l'étape est terminée, le De envoie une interface d' [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) au SDM, qui est un événement arrêtant.  
  
 Si l'utilisateur choisit de poursuivre l'exécution du pointeur d'instruction actuel, l'IDE demande au SDM d'appeler [IDebugProgram2 : : exécutez](../../extensibility/debugger/reference/idebugprogram2-execute.md).  Le programme l'exécution se poursuit jusqu'à ce qu'il rencontre l'état arrêtant suivant.  
  
 Si le package de débogage est ignoré un événement arrêtant particulier, le package de débogage appelle le SDM, qui appelle [IDebugProgram2 : : continuez](../../extensibility/debugger/reference/idebugprogram2-continue.md).  Si le programme faisait pas \- à \- pas, sur, ou à partir d'une fonction lorsqu'il a rencontré la condition cessante, il reprend l'étape.  Cela implique que le programme effectue un rapport de progression, de sorte qu'il soit continuer.  
  
 Les appels que le SDM fait à `Step`, **Exécuter**, et **Continuer** sont asynchrone, ce qui signifie que le SDM s'attend à ce que l'appel est retourné rapidement.  Si le De envoie le SDM un événement arrêtant sur le même thread avant `Step`, retourne la valeur d' **Exécuter**, ou de **Continuer** , le SDM bloque.  
  
## Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)