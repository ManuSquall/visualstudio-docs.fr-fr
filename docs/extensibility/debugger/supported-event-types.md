---
title: Types d’événements pris en charge (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712798"
---
# <a name="supported-event-types"></a>Types d’événements soutenus
Le débogage Visual Studio prend actuellement en charge les types d’événements suivants :

- Événements asynchrones

   Notez au gestionnaire de débogé de session (SDM) et à l’IDE que l’état de la demande de débogé est en train de changer. Ces événements sont traités au loisir du SDM et de l’IDE. Aucune réponse n’est envoyée au moteur de débogé (DE) une fois l’événement traité. Les interfaces [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) et [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sont des exemples d’événements asynchrones.

- Événements synchrones

   Informez le SDM et l’IDE que l’état de l’application en cours de déboiffée est en train de changer. La seule différence entre ces événements et les événements asynchrones est qu’une réponse est envoyée au moyen de la méthode [ContinueDeromSynchroneEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   L’envoi d’un événement synchrone est utile si vous avez besoin de votre DE pour continuer à traiter après que l’IDE a reçu et traite l’événement.

- Arrêt synchrone ou arrêt des événements

   Notez au SDM et à l’IDE que l’application en cours de déboiffage a cessé d’exécuter le code. Lorsque vous envoyez un événement d’arrêt au moyen de la méthode [Événement](../../extensibility/debugger/reference/idebugeventcallback2-event.md), le [paramètre IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) est nécessaire. Les événements d’arrêt se poursuivent par un appel à l’une des méthodes suivantes :

  - [Exécuter](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Étape](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuer](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’événements d’arrêt.

  > [!NOTE]
  > Les événements d’arrêt asynchrones ne sont pas pris en charge. C’est une erreur d’envoyer un événement d’arrêt asynchrone.

## <a name="discussion"></a>Discussions
 La mise en œuvre réelle des événements dépend de la conception de votre DE. Le type de chaque événement envoyé est déterminé par ses attributs, qui sont définis lorsque vous concevez le DE. Par exemple, un DE peut envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) comme un événement asynchrone, tandis qu’un autre peut l’envoyer comme un événement d’arrêt.

 Le tableau suivant précise quels paramètres de programme et de thread sont nécessaires pour quels événements, ainsi que les types d’événements. Tout événement peut être synchrone. Aucun événement n’a besoin d’être synchrone.

> [!NOTE]
> [L’interface IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) est requise pour tous les événements.

|Événement|IDebugProgram2|IDebugThread2|Arrêt des événements|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non autorisé|Non autorisé|Non|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non autorisé|Non autorisé|Non|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Peut être|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Peut être|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Peut être|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatoire|Autorisé, mais pas requis|Non|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatoire|Autorisé, mais pas requis|Non|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatoire|Autorisé, mais pas requis|Non|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatoire|Autorisé, mais pas requis|Non|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatoire|Autorisé, mais pas requis|Non|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|IDebugStopCompleteEvent2|Obligatoire|Obligatoire|Oui|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatoire|Obligatoire|Oui|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatoire|Obligatoire|Non|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Autorisé, mais pas requis|Autorisé, mais pas requis|Non|

## <a name="see-also"></a>Voir aussi
- [Envoi des événements](../../extensibility/debugger/sending-events.md)
