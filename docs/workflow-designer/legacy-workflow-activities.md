---
title: Concepteur de flux de travail - activités de Workflow hérité
ms.date: 01/18/2017
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c24c0be518e58ce87af11a38486818ca4a3ac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979475"
---
# <a name="legacy-workflow-activities"></a>Activités de workflow héritées

Windows Workflow Foundation (WF) inclut un ensemble par défaut des activités qui fournissent des fonctionnalités de flux de contrôle, conditions, la gestion des événements, la gestion d’état et communiquer avec les applications et services. Lors de la conception de flux de travail, vous pouvez utiliser les activités fournies par le système qui sont fournies par le Concepteur de flux de travail Windows, ou vous pouvez créer vos propres activités personnalisées.

Le tableau suivant répertorie les activités prédéfinies de l'infrastructure Windows Workflow Foundation. Nombre, mais pas tous, de ces activités sont représentées par les concepteurs d’activités qui sont accessibles à partir de la **boîte à outils** du Concepteur de Workflow. Pour créer une activité, faites glisser son concepteur à partir de la **boîte à outils** et déposez-la sur l’aire de conception.

|Activité|Description|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Utilisé avec le **HandleExternalEventActivity** activité pour les communications entrantes et sortantes avec un service local. Pour plus d’informations, consultez [à l’aide de l’activité CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Utilisée pour contenir la logique de nettoyage (une activité composite a été annulée avant que l'exécution de tous les enfants de l'activité composite ne soit terminée). Pour plus d’informations, consultez [à l’aide de l’activité CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Permet d'ajouter un code Visual Basic ou C# à votre workflow. Pour plus d’informations, consultez [à l’aide de l’activité CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Version compensable de l'activité <xref:System.Workflow.Activities.SequenceActivity>. Pour plus d’informations, consultez [à l’aide de l’activité CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Une version compensable de **TransactionScopeActivity**. Pour plus d’informations, consultez [à l’aide de l’activité CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Permet d'appeler le code utilisé pour annuler ou compenser les opérations déjà exécutées par le workflow lorsqu'une erreur se produit. Pour plus d’informations, consultez [à l’aide de l’activité CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Wrapper pour une ou plusieurs activités qui effectuent une compensation pour une activité TransactionScopeActivity terminée. pour plus d’informations, consultez [à l’aide de l’activité CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Exécute les activités enfants basées sur une condition qui s'applique à l'activité <xref:System.Workflow.Activities.ConditionedActivityGroup> elle-même et selon les conditions qui s'appliquent séparément à chaque activité enfant. Pour plus d’informations, consultez [à l’aide de l’activité ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Permet de générer des délais dans votre workflow sur la base d'un intervalle de délai d'attente. Pour plus d’informations, consultez [à l’aide de l’activité DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Encapsule une ou plusieurs activités exécutées lorsqu'un événement spécifié se produit. Pour plus d’informations, consultez [à l’aide de l’activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Fournit une infrastructure permettant d'associer des événements à une activité. Pour plus d’informations, consultez [à l’aide de l’activité EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Exécute son activité enfant principale simultanément avec un <xref:System.Workflow.Activities.EventHandlersActivity>. Pour plus d’informations, consultez [à l’aide de l’activité EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Utilisée pour gérer une exception d'un type que vous spécifiez. Pour plus d’informations, consultez [à l’aide de l’activité FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Représente une activité composite qui possède une liste ordonnée d’activités enfants de type **System.Workflow.Activities.FaultHandlerActivity**. Pour plus d’informations, consultez [à l’aide de l’activité FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Utilisée conjointement avec la <xref:System.Workflow.Activities.CallExternalMethodActivity> activité pour les communications entrantes et sortantes avec un service local. Pour plus d’informations, consultez [à l’aide de l’activité HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Teste une condition sur chaque branche et exécute des activités sur la première branche pour laquelle la condition est égal à **true**. Pour plus d’informations, consultez [à l’aide de l’activité IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Représente une branche d'une <xref:System.Workflow.Activities.IfElseActivity>. Pour plus d’informations, consultez [à l’aide de l’activité IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Permet à votre workflow d'appeler un service Web. Pour plus d’informations, consultez [à l’aide de l’activité d’une activité InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Permet à votre workflow d'appeler un autre workflow. Pour plus d’informations, consultez [à l’aide de l’activité de l’activité InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Activité composite qui contient uniquement des activités enfants <xref:System.Workflow.Activities.EventDrivenActivity>. Pour plus d’informations, consultez [à l’aide de l’activité de l’activité ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Fournit une méthode de planification de deux ou plusieurs enfants **SequenceActivity** branches d’activité pour le traitement en même temps. Pour plus d’informations, consultez [à l’aide de l’activité ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|S’utilise pour représenter une collection de règles. Une règle se compose de conditions et des actions qui en résultent. Pour plus d’informations, consultez [à l’aide de l’activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Crée plusieurs instances d'une activité enfant unique. Pour plus d’informations, consultez [à l’aide de l’activité ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Constitue une méthode simple de liaison de plusieurs activités en vue d'une exécution séquentielle. Pour plus d’informations, consultez [à l’aide de l’activité SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Spécifie une transition vers un nouvel état. Pour plus d’informations, consultez [à l’aide de l’activité SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Représente un état au sein d'un workflow d'ordinateur d'état. Pour plus d’informations, consultez [à l’aide de l’activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Utilisé dans un <xref:System.Workflow.Activities.StateActivity> activité en tant que conteneur pour les activités enfants qui sont exécutées lorsque la **StateActivity** activité. Pour plus d’informations, consultez [à l’aide de l’activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Utilisé dans un <xref:System.Workflow.Activities.StateActivity> activité en tant que conteneur pour les activités enfants qui sont exécutées lorsque la **StateActivity** activité. Pour plus d’informations, consultez [à l’aide de l’activité StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Interrompt le fonctionnement de votre workflow pour activer une intervention lorsqu'un événement requiert une attention spécifique. Pour plus d’informations, consultez [à l’aide de l’activité SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Exécute séquentiellement des activités contenues dans un domaine synchronisé. Pour plus d’informations, consultez [à l’aide de l’activité SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Permet de mettre fin immédiatement à l'opération effectuée par votre workflow en cas d'erreur. Pour plus d’informations, consultez [à l’aide de l’activité TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Permet de capturer les exceptions métier levées dans le cadre des métadonnées de processus d'un workflow. Pour plus d’informations, consultez [à l’aide de l’activité ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Fournit une infrastructure pour la gestion des transactions et des exceptions. Pour plus d’informations, consultez [à l’aide de l’activité TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Permet de modéliser l'occurrence d'une erreur de service Web. Pour plus d’informations, consultez [à l’aide de l’activité WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Reçoit des données en provenance d'un service Web. Pour plus d’informations, consultez [à l’aide de l’activité WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Répond à une demande de service Web faite à un workflow. Pour plus d’informations, consultez [à l’aide de l’activité WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Permet à votre workflow d'exécuter une boucle jusqu'à ce qu'une condition donnée soit remplie. Pour plus d’informations, consultez [à l’aide de l’activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

Pour plus d’informations sur la création d’activités personnalisées, consultez [développement d’activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65023) et [à l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>Voir aussi

- [Activités Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)
- [Développement de flux de travail](http://go.microsoft.com/fwlink?LinkID=65010)
- [Développement des activités de flux de travail](http://go.microsoft.com/fwlink?LinkID=65023)