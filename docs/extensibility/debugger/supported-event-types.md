---
title: Types d’événements pris en charge | Microsoft Docs
description: Découvrez les types d’événements pris en charge par le débogage Visual Studio, y compris les événements asynchrones, les événements synchrones et les événements d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fff86a142f541c1b17012b6190dd68e8d5628a3c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902902"
---
# <a name="supported-event-types"></a>Types d’événements pris en charge
Le débogage Visual Studio prend actuellement en charge les types d’événements suivants :

- Événements asynchrones

   Notifiez le gestionnaire de débogage de session (SDM) et l’IDE que l’état de l’application en cours de débogage est en cours de modification. Ces événements sont traités à la une des loisirs du SDM et de l’IDE. Aucune réponse n’est envoyée au moteur de débogage (DE) une fois l’événement traité. Les interfaces [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) et [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sont des exemples d’événements asynchrones.

- Événements synchrones

   Informez le SDM et l’IDE que l’état de l’application en cours de débogage change. La seule différence entre ces événements et les événements asynchrones est qu’une réponse est envoyée à l’aide de la méthode [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

   L’envoi d’un événement synchrone est utile si vous avez besoin que votre DE continue son traitement après réception et traitement de l’événement par l’IDE.

- Événements d’arrêt synchrones ou événements d’arrêt

   Notifiez le SDM et l’IDE que l’application en cours de débogage a cessé d’exécuter le code. Lorsque vous envoyez un événement d’arrêt à l’aide de l' [événement](../../extensibility/debugger/reference/idebugeventcallback2-event.md)de méthode, le paramètre [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) est requis. Les événements d’arrêt sont poursuivis par un appel à l’une des méthodes suivantes :

  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Étape](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuer](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’événements d’arrêt.

  > [!NOTE]
  > Les événements d’arrêt asynchrones ne sont pas pris en charge. L’envoi d’un événement d’arrêt asynchrone est une erreur.

## <a name="discussion"></a>Discussion
 L’implémentation réelle des événements dépend de la conception de votre. Le type de chaque événement envoyé est déterminé par ses attributs, qui sont définis quand vous concevez le DE. Par exemple, un DE peut envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) en tant qu’événement asynchrone, tandis qu’un autre peut l’envoyer en tant qu’événement d’arrêt.

 Le tableau suivant spécifie les paramètres de programme et de thread requis pour les événements, ainsi que les types d’événements. Tout événement peut être synchrone. Aucun événement ne doit être synchrone.

> [!NOTE]
> L’interface [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) est requise pour tous les événements.

|Événement|IDebugProgram2|IDebugThread2|Arrêt des événements|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non autorisé|Non autorisé|Non|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non autorisé|Non autorisé|Non|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Peut être|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Peut être|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Peut être|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|IDebugStopCompleteEvent2|Obligatoire|Obligatoire|Oui|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Autorisé, mais pas obligatoire|Autorisé, mais pas obligatoire|Non|

## <a name="see-also"></a>Voir aussi
- [Envoi des événements](../../extensibility/debugger/sending-events.md)
