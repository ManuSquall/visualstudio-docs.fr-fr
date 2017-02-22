---
title: "Types d&#39;&#233;v&#233;nements pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), prise en charge des événements"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Types d&#39;&#233;v&#233;nements pris en charge
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio débogage actuellement prend en charge les types suivants d'événement :  
  
-   événements asynchrones  
  
     Indiquez au gestionnaire et IDE \(SDM\) de débogage de session que l'état de l'application qui est déboguée change.  Ces événements sont traités aux souhaitez du SDM et de l'IDE.  Absence de réponse n'est envoyée au moteur \(DE\) de débogage une fois que l'événement est traité.  Les interfaces d' [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) et d' [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sont des exemples d'événements asynchrones.  
  
-   événements synchrones  
  
     Indiquez au SDM et l'IDE que l'état de l'application qui est déboguée change.  la seule différence entre ces événements et événements asynchrones est qu'une réponse est envoyée au moyen de la méthode d' [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)  
  
     Envoyer un événement synchrone est utile si vous avez besoin de votre De pour poursuivre le traitement après l'IDE reçoit et traite l'événement.  
  
-   Événements cessants synchrones, ou arrêter des événements  
  
     Indiquez au SDM et IDE que l'application est déboguée a cessé d'exécuter le code.  Lorsque vous envoyez un événement arrêtant au moyen de la méthode [Événement](../../extensibility/debugger/reference/idebugeventcallback2-event.md), le paramètre d' [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) est requis.  Arrêt des événements sont repris par un appel à celui des méthodes suivantes :  
  
    -   [Exécuter](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Étape](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continuer](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d'événements d'arrêt.  
  
    > [!NOTE]
    >  Les événements cessants asynchrones ne sont pas pris en charge.  Il est erroné d'envoyer un événement arrêtant asynchrone.  
  
## Discussion  
 L'implémentation réelle des événements dépend de celle de votre De.  Le type de chaque événement envoyé est déterminé par ses attributs, qui sont définis lorsque vous concevez le De.  Par exemple, un De peut envoyer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) en tant qu'événement asynchrone, alors que les autres peuvent envoyer comme un événement arrêtant.  
  
 Le tableau suivant spécifie qui programment et il requiert des paramètres de thread pour lesquels les événements, ainsi que l'événement types.  Tout événement soit synchrone.  aucun événement ne doit être synchrone.  
  
> [!NOTE]
>  l'interface d' [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) est requise pour tous les événements.  
  
|Événement|IDebugProgram2|IDebugThread2|Empêcher les événements|  
|---------------|--------------------|-------------------|-----------------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non autorisé|Non autorisé|Non|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non autorisé|Non autorisé|Non|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|peut être|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|peut être|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|peut être|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|IDebugStopCompleteEvent2|Obligatoire|Obligatoire|Oui|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Non|  
  
## Voir aussi  
 [L'envoi d'événements](../../extensibility/debugger/sending-events.md)