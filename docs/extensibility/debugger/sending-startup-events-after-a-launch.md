---
title: "L&#39;envoi d&#39;&#233;v&#233;nements de d&#233;marrage apr&#232;s le lancement d&#39;un | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], les événements de démarrage"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# L&#39;envoi d&#39;&#233;v&#233;nements de d&#233;marrage apr&#232;s le lancement d&#39;un
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une fois que le \(DE\) moteur de débogage est attaché au programme, il envoie une série d'événements de démarrage dans la session de débogage.  
  
 Les événements de démarrage envoyés arrière à la session de débogage sont les suivants :  
  
-   Un événement de création du moteur.  
  
-   Un événement de création du programme.  
  
-   événements de création et de chargement du module de thread.  
  
-   Un événement terminé de charge, envoyé lorsque le code est chargé et prêt à être exécuté, mais avant que tout code soit exécuté  
  
    > [!NOTE]
    >  Lorsque cet événement est repris, des variables globales sont initialisés et le passage de routines de démarrage.  
  
-   autre possible événements de création et de chargement du module de thread.  
  
-   Un événement point d'entrée, qui signale que le programme a atteint son point d'entrée principal, tel que **Main** ou `WinMain`.  Cet événement n'est généralement pas envoyé si le De est attaché à un programme qui s'exécute déjà.  
  
 Par programme, le De envoie en premier le gestionnaire de débogage de session qu' \(SDM\)une interface d' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , qui représente un événement de création du moteur, suivi [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), qui représente un événement de création du programme.  
  
 Cela est généralement suivi d'un ou plusieurs événements d'événements de création de thread d' [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) et de chargement du module d' [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
 Lorsque le code est chargé et prêt à être exécuté, mais avant que tout le code est exécuté, le De envoie le SDM un événement terminé de charge d' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) .  Enfin, si le programme n'est pas déjà, le De envoie un événement point d'entrée d' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , qui signale que le programme a atteint son point d'entrée principal et est prêt pour le débogage.  
  
## Voir aussi  
 [Contrôle de l'exécution](../../extensibility/debugger/control-of-execution.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)