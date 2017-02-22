---
title: "Concepteur d&#39;activit&#233;s InitializeCorrelation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s InitializeCorrelation
Le concepteur d'activités **InitializeCorrelation** permet de créer et configurer une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> utilisée pour établir une corrélation entre des messages avant leur envoi ou leur réception.  
  
## Activité InitializeCorrelation  
 Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message.En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message.Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.  
  
### Utilisation du concepteur d'activités InitializeCorrelation  
 Le concepteur d'activités **InitializeCorrelation** se trouve dans la catégorie **Messagerie** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **InitializeCorrelation** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Cette action crée une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> avec InitializeCorrelation comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **InitializeCorrelation** ou dans la zone **DisplayName** de la fenêtre **Propriétés**.  
  
 L'objet <xref:System.ServiceModel.Activities.CorrelationHandle> peut être spécifié dans le champ **Corrélation** dans la fenêtre **Propriétés** dans l'aire du concepteur de l'activité **InitializeCorrelation**.  
  
 Cliquez sur le bouton de sélection situé en regard du champ **CorrelationData** dans la fenêtre **Propriétés** ou sur le texte d'indication « Afficher... » dans l'aire du concepteur de l'activité **InitializeCorrelation** pour afficher la boîte de dialogue **Initialiser la corrélation** dans laquelle vous pouvez spécifier le gestionnaire de corrélation et les paires clé\-valeur utilisées pour l'initialiser.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette boîte de dialogue, consultez la rubrique [Boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md).  
  
### Propriétés d'InitializeCorrelation  
 Le tableau suivant présente les propriétés d'<xref:System.ServiceModel.Activities.InitializeCorrelation> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez la boîte de dialogue **Initialiser la corrélation** pour configurer <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette boîte de dialogue, consultez la rubrique [Boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md).|  
  
## Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyez](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)