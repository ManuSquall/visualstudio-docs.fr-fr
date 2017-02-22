---
title: "Lancement du d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), le lancement du débogueur"
  - "lancer le débogueur (débogage SDK),"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Lancement du d&#233;bogueur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lancer le débogueur requiert l'envoi la séquence correcte d'événements et de méthodes avec leurs attributs appropriés.  
  
## Séquences d'événements et de méthodes  
  
1.  Le gestionnaire de débogage de session \(SDM\) est appelé en choisissant le menu de **Débogage** , puis choisissez **Démarrer**.  Consultez [Lancement d'un programme](../../extensibility/debugger/launching-a-program.md) pour plus d'informations.  
  
2.  Le SDM appelle la méthode d' [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
3.  Selon le modèle \(DE\) de processus du moteur de débogage, la méthode d' `IDebugProgramNodeAttach2::OnAttach` retourne une des méthodes suivantes, qui détermine les étapes suivantes.  
  
     si `S_FALSE` est retourné, le moteur de débogage \(DE\) doit être chargé en cours de l'ordinateur virtuel.  
  
     ou  
  
     si `S_OK` est retourné, le De doit être chargé en cours du SDM.  Le SDM effectue les tâches suivantes :  
  
    1.  Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur du De.  
  
    2.  crée le De.  
  
    3.  appelle [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Le De envoie [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
5.  Le De envoie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
6.  Le De envoie [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
7.  Le De envoie [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
8.  Le De envoie [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)   
 [Lancement d'un programme](../../extensibility/debugger/launching-a-program.md)