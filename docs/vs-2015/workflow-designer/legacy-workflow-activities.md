---
title: Activités de flux de travail héritées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302952"
---
# <a name="legacy-workflow-activities"></a>Activités de workflow héritées
[!INCLUDE[wf](../includes/wf-md.md)] comprend un ensemble d’activités par défaut qui fournissent des fonctionnalités pour le workflow de contrôle, les conditions, la gestion des événements, la gestion d’État et la communication avec les applications et les services. Lorsque vous concevez des workflows, vous pouvez utiliser les activités fournies par le système via [!INCLUDE[wfd1](../includes/wfd1-md.md)], ou vous pouvez créer vos propres activités personnalisées.

 Le tableau suivant répertorie les activités prédéfinies de l'infrastructure [!INCLUDE[wf2](../includes/wf2-md.md)]. La plupart de ces activités sont représentées par des concepteurs d’activités accessibles à partir de la **boîte à outils** de l' [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Pour créer une activité, faites glisser son concepteur de la **boîte à outils** et déposez-la sur l’aire de conception.

|Activité|Description|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Utilisé avec l’activité **HandleExternalEventActivity** pour les communications d’entrée et de sortie avec un service local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Utilisée pour contenir la logique de nettoyage (une activité composite a été annulée avant que l'exécution de tous les enfants de l'activité composite ne soit terminée). [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Permet d'ajouter un code Visual Basic ou C# à votre workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|Version compensable de [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|Version compensable de **activité TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Permet d'appeler le code utilisé pour annuler ou compenser les opérations déjà exécutées par le workflow lorsqu'une erreur se produit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Wrapper pour une ou plusieurs activités qui effectuent une compensation pour une activité activité TransactionScopeActivity terminée [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Exécute des activités enfants basées sur une condition qui s’applique à l’activité [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) elle-même et selon les conditions qui s’appliquent séparément à chaque enfant. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|Permet de générer des délais dans votre workflow sur la base d'un intervalle de délai d'attente. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité DelayActivity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Encapsule une ou plusieurs activités exécutées lorsqu'un événement spécifié se produit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Fournit une infrastructure permettant d'associer des événements à une activité. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[Activité EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Exécute son activité enfant principale simultanément avec un [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité activité EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Utilisée pour gérer une exception d'un type que vous spécifiez. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Représente une activité composite qui possède une liste ordonnée d’activités enfants de type [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Utilisé conjointement avec l’activité [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) pour les communications d’entrée et de sortie avec un service local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Teste une condition sur chaque branche et exécute des activités sur la première branche pour laquelle la condition est égale à **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Représente une branche d’un [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Permet à votre workflow d'appeler un service Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Permet à votre workflow d'appeler un autre workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|Activité composite qui contient uniquement des activités enfants [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité ListenActivity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Offre un moyen de planifier plusieurs branches d’activité **SequenceActivity** enfants à traiter en même temps. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|S’utilise pour représenter une collection de règles. Une règle se compose de conditions et des actions qui en résultent. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Crée plusieurs instances d'une activité enfant unique. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Constitue une méthode simple de liaison de plusieurs activités en vue d'une exécution séquentielle. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Spécifie une transition vers un nouvel état. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Représente un état au sein d'un workflow d'ordinateur d'état. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Utilisé dans une activité [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) comme conteneur pour les activités enfants exécutées lors de la sortie de l’activité **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Utilisé dans une activité [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) comme conteneur pour les activités enfants exécutées lors de l’entrée dans l’activité **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Interrompt le fonctionnement de votre workflow pour activer une intervention lorsqu'un événement requiert une attention spécifique. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Exécute séquentiellement des activités contenues dans un domaine synchronisé. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Permet de mettre fin immédiatement à l'opération effectuée par votre workflow en cas d'erreur. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|Permet de capturer les exceptions métier levées dans le cadre des métadonnées de processus d'un workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[Activité TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Fournit un cadre pour la gestion des transactions et des exceptions. Pour plus d’informations, consultez [utilisation de l’activité activité TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Permet de modéliser l'occurrence d'une erreur de service Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Reçoit des données en provenance d'un service Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Répond à une demande de service Web faite à un workflow. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Permet à votre workflow d'exécuter une boucle jusqu'à ce qu'une condition donnée soit remplie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][à l’aide de l’activité WhileActivity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] comment créer des activités personnalisées, consultez [développement d’activités personnalisées](https://go.microsoft.com/fwlink?LinkID=65023) et [utilisation du concepteur d’activités héritées](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Dans cette section
 [Vues d’activité (héritées)](../workflow-designer/activity-views-legacy.md) Décrit les différentes vues de conception des activités.

 [Comment : ajouter des activités à la boîte à outils (héritée)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Montre comment ajouter des activités à la boîte à outils.

 [Comment : créer une condition de règle déclarative (héritée)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Montre les étapes permettant de créer une condition de règle déclarative.

 [Procédure : créer un ensemble de règles PolicyActivity (hérité)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Montre les étapes permettant de créer un ensemble de règles PolicyActivity.

 [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Montre les étapes permettant d’implémenter une opération de contrat de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

 [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Montre les étapes permettant d’appeler une opération de contrat de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Voir aussi
 [Activités de Windows Workflow Foundation](https://go.microsoft.com/fwlink?LinkID=65005) [développement de workflows](https://go.microsoft.com/fwlink?LinkID=65010) [développement d’activités de flux de travail](https://go.microsoft.com/fwlink?LinkID=65023)