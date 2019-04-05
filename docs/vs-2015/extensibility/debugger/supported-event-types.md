---
title: Prise en charge des Types d’événements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82bce8546d4c63a82f4850097ca92c804399a66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953574"
---
# <a name="supported-event-types"></a>Types d’événements pris en charge
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Débogage de Visual Studio prend actuellement en charge les types d’événements suivants :  
  
- Événements asynchrones  
  
   Notifier le Gestionnaire de session de débogage (SDM) et l’IDE qui change l’état de l’application en cours de débogage. Ces événements sont traités à la convenance du SDM et l’IDE. Aucune réponse n’est envoyée au moteur de débogage (dé) une fois que l’événement est traité. Le [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) et [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfaces sont des exemples d’événements asynchrones.  
  
- Événements synchrones  
  
   Notifier le SDM et l’IDE que la modification de l’état de l’application en cours de débogage. La seule différence entre ces événements et les événements asynchrones est qu’une réponse est envoyée par le biais de la [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) (méthode).  
  
   Envoyer un événement synchrone est utile si vous avez besoin de votre DE poursuivre le traitement une fois que l’IDE reçoit et traite l’événement.  
  
- Les événements d’arrêt synchrones, ou que les événements d’arrêt  
  
   Notifier le SDM et l’IDE que l’application en cours de débogage s’est arrêté l’exécution de code. Lorsque vous envoyez un événement d’arrêt au moyen de la méthode [événement](../../extensibility/debugger/reference/idebugeventcallback2-event.md), le [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) paramètre est obligatoire. Événements d’arrêt sont maintenues par un appel à l’une des méthodes suivantes :  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’événements d’arrêt.  
  
  > [!NOTE]
  >  Événements d’arrêt asynchrone ne sont pas pris en charge. C’est une erreur pour envoyer un événement d’arrêt asynchrone.  
  
## <a name="discussion"></a>Discussion  
 L’implémentation réelle des événements dépend de la conception de votre DE. Le type de chaque événement envoyé est déterminé par ses attributs, qui sont définis lorsque vous concevez l’Allemagne. Par exemple, un dé peut envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) comme un événement asynchrone, tandis que l’autre peut l’envoyer comme un événement d’arrêt.  
  
 Le tableau suivant spécifie les paramètres de programme et de thread sont nécessaires pour les événements, ainsi que les types d’événements. N’importe quel événement peut être synchrone. Aucun événement ne doit être synchrone.  
  
> [!NOTE]
>  Le [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interface est requise pour tous les événements.  
  
|Événement|IDebugProgram2|IDebugThread2|Les événements d’arrêt|  
|-----------|--------------------|-------------------|---------------------|  
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
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Peut être|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Peut être|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatoire|Obligatoire|Oui|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Autorisée, mais pas obligatoire|Autorisée, mais pas obligatoire|Peut être|  
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
  
## <a name="see-also"></a>Voir aussi  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)
