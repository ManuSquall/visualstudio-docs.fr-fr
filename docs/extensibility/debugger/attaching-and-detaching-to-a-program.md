---
title: "Attachement et d&#233;tachement d&#39;un programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, attacher aux programmes"
  - "moteurs de débogage, le détachement de programmes"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Attachement et d&#233;tachement d&#39;un programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Attacher le débogueur requiert l'envoi la séquence correcte d'événements et de méthodes avec les attributs appropriés.  
  
## séquence de méthodes et d'événements  
  
1.  le gestionnaire de débogage de session \(SDM\) appelle la méthode d' [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
     Selon le modèle \(DE\) de processus du moteur de débogage, la méthode d' `IDebugProgramNodeAttach2::OnAttach` retourne une des méthodes suivantes, qui détermine les étapes suivantes.  
  
     Si `S_FALSE` est retourné, le moteur de débogage a été correctement attaché au programme.  Sinon, la méthode d' [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée pour exécuter le processus d'attachement.  
  
     si `S_OK` est retourné, le De doit être chargé dans le même processus que le SDM.  Le SDM effectue les tâches suivantes :  
  
    1.  Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur du De.  
  
    2.  crée le De.  
  
    3.  appelle [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Le De envoie [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
3.  Le De envoie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM avec un attribut d' `EVENT_SYNC` .  
  
4.  Le De envoie [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM avec un attribut d' `EVENT_SYNC_STOP` .  
  
 Détacher un programme est un simple, processus de pas de deux, comme suit :  
  
1.  Le SDM appelle [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Le De envoie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)