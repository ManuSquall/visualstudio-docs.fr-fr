---
title: "Prise en charge des Types d’événements | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d161b078e4001ea7f02311bbcefe4c7f1eb6b7b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="supported-event-types"></a>Types d’événements pris en charge
Débogage de Visual Studio prend actuellement en charge les types d’événements suivants :  
  
-   Événements asynchrones  
  
     Notifier le Gestionnaire de session de débogage (SDM) et IDE qui modifie l’état de l’application en cours de débogage. Ces événements sont traités à la convenance du SDM et l’IDE. Aucune réponse n’est envoyée au moteur de débogage (DE) une fois que l’événement est traité. Le [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) et [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfaces sont des exemples d’événements asynchrones.  
  
-   Événements synchrones  
  
     Informez le SDM et IDE qui modifie l’état de l’application en cours de débogage. La seule différence entre ces événements et les événements asynchrones est qu’une réponse est envoyée à l’aide de la [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) (méthode).  
  
     L’envoi d’un événement synchrone est utile si vous avez besoin de votre DE poursuivre le traitement une fois que l’IDE reçoit et traite l’événement.  
  
-   Les événements d’arrêt synchrones, ou les événements d’arrêt  
  
     Notifier le SDM et l’IDE que l’application en cours de débogage a arrêté l’exécution de code. Lorsque vous envoyez un événement d’arrêt au moyen de la méthode [événement](../../extensibility/debugger/reference/idebugeventcallback2-event.md), le [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) paramètre est obligatoire. Événements d’arrêt sont maintenues par un appel à l’une des méthodes suivantes :  
  
    -   [Exécuter](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’événements d’arrêt.  
  
    > [!NOTE]
    >  Événements d’arrêt asynchrone ne sont pas pris en charge. Il s’agit d’une erreur pour envoyer un événement d’arrêt asynchrone.  
  
## <a name="discussion"></a>Discussion  
 L’implémentation réelle des événements dépend de la conception de votre DE. Le type de chaque événement envoyé est déterminé par ses attributs, qui sont définis lorsque vous concevez le DE. Par exemple, un seul DE peut envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) comme un événement asynchrone, tandis que l’autre peut l’envoyer en tant qu’un événement d’arrêt.  
  
 Le tableau suivant spécifie les paramètres de programme et les threads sont requises pour les événements, ainsi que les types d’événements. Les événements peuvent être synchrones. Aucun événement ne doit être synchrone.  
  
> [!NOTE]
>  Le [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interface est requise pour tous les événements.  
  
|événement|IDebugProgram2|IDebugThread2|Les événements d’arrêt|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non autorisé|Non autorisé|Non|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non autorisé|Non autorisé|Non|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Peut être|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Peut être|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Peut être|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatoire|Autorisée, mais non requis|Non|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatoire|Autorisée, mais non requis|Non|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatoire|Autorisée, mais non requis|Non|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatoire|Autorisée, mais non requis|Non|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatoire|Autorisée, mais non requis|Non|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|IDebugStopCompleteEvent2|Obligatoire|Obligatoire|Oui|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatoire|Obligatoire|Non|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Autorisée, mais non requis|Autorisée, mais non requis|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)