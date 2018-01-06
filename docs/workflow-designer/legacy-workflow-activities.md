---
title: "Activités de Workflow hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 756fa86cf892120b0062e2816f146425ac1b4fa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-workflow-activities"></a>Activités de workflow héritées
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] inclut un ensemble d'activités par défaut qui fournit les fonctionnalités utilisées pour le flux de contrôle, les conditions, la gestion des événements, la gestion des états et pour communiquer avec les applications et les services. Lorsque vous concevez des workflows, vous pouvez utiliser les activités fournies par le système via [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], ou vous pouvez créer vos propres activités personnalisées.  
  
 Le tableau suivant répertorie les activités prédéfinies de l'infrastructure [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Nombre, mais pas tous, de ces activités sont représentées par les concepteurs d’activités qui sont accessibles à partir de la **boîte à outils** de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Pour créer une activité, faites glisser son concepteur à partir de la **boîte à outils** et déposez-la sur l’aire de conception.  
  
|Activité|Description|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Utilisé avec le **HandleExternalEventActivity** activité pour les communications entrantes et sortantes avec un service local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[Activité CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Utilisée pour contenir la logique de nettoyage (une activité composite a été annulée avant que l'exécution de tous les enfants de l'activité composite ne soit terminée). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Permet d'ajouter un code Visual Basic ou C# à votre workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Une version compensable de [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Une version compensable de **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Activité CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Permet d'appeler le code utilisé pour annuler ou compenser les opérations déjà exécutées par le workflow lorsqu'une erreur se produit. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Wrapper pour une ou plusieurs activités qui effectuent une compensation pour une activité TransactionScopeActivity terminée [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [à l’aide de l’activité CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Exécute les activités enfants basées sur une condition qui s’applique à la [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) activité elle-même et selon les conditions qui s’appliquent séparément à chacun d’eux. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Permet de générer des délais dans votre workflow sur la base d'un intervalle de délai d'attente. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Encapsule une ou plusieurs activités exécutées lorsqu'un événement spécifié se produit. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fournit une infrastructure permettant d'associer des événements à une activité. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Exécute son activité enfant principale simultanément avec un [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Utilisée pour gérer une exception d'un type que vous spécifiez. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Représente une activité composite qui possède une liste ordonnée d’activités enfants de type [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Utilisée conjointement avec la [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) activité pour les communications entrantes et sortantes avec un service local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Teste une condition sur chaque branche et exécute des activités sur la première branche pour laquelle la condition est égal à **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Représente une branche d’un [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[Activité InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Permet à votre workflow d'appeler un service Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité d’une activité InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[Activité InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Permet à votre workflow d'appeler un autre workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité de l’activité InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[Activité ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Une activité composite qui contient uniquement [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) activités enfants. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité de l’activité ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Fournit une méthode de planification de deux ou plusieurs enfants **SequenceActivity** branches d’activité pour le traitement en même temps. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|S’utilise pour représenter une collection de règles. Une règle se compose de conditions et des actions qui en résultent. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][À l’aide de l’activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crée plusieurs instances d'une activité enfant unique. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Constitue une méthode simple de liaison de plusieurs activités en vue d'une exécution séquentielle. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Spécifie une transition vers un nouvel état. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Représente un état au sein d'un workflow d'ordinateur d'état. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Utilisé dans un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) activité en tant que conteneur pour les activités enfants qui sont exécutées lorsque la **StateActivity** activité. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Utilisé dans un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) activité en tant que conteneur pour les activités enfants qui sont exécutées lorsque la **StateActivity** activité. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Interrompt le fonctionnement de votre workflow pour activer une intervention lorsqu'un événement requiert une attention spécifique. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Exécute séquentiellement des activités contenues dans un domaine synchronisé. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Permet de mettre fin immédiatement à l'opération effectuée par votre workflow en cas d'erreur. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Permet de capturer les exceptions métier levées dans le cadre des métadonnées de processus d'un workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[Activité TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fournit une infrastructure pour la gestion des transactions et des exceptions. Pour plus d’informations, consultez [à l’aide de l’activité TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Permet de modéliser l'occurrence d'une erreur de service Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Reçoit des données en provenance d'un service Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Répond à une demande de service Web faite à un workflow. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[Activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Permet à votre workflow d'exécuter une boucle jusqu'à ce qu'une condition donnée soit remplie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilisation de l’activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]comment créer des activités personnalisées, consultez [développement d’activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65023) et [à l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vues Activité (hérité)](../workflow-designer/activity-views-legacy.md)  
 Décrit les différents modes Design des activités.  
  
 [Guide pratique pour ajouter des activités à la boîte à outils (hérité)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Indique comment ajouter des activités à la boîte à outils.  
  
 [Guide pratique pour créer une condition de règle déclarative (hérité)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Affiche les étapes à suivre pour créer une condition de règle déclarative.  
  
 [Guide pratique pour créer un ensemble de règles PolicyActivity (hérité)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Affiche les étapes à suivre pour créer un ensemble de règles PolicyActivity.  
  
 [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Affiche les étapes à suivre pour implémenter une opération de contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
 [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Affiche les étapes à suivre pour appeler une opération de contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Activités Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Développement de flux de travail](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Développement des activités de flux de travail](http://go.microsoft.com/fwlink?LinkID=65023)