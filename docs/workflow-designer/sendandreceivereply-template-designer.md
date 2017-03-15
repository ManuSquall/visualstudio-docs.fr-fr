---
title: "Concepteur de mod&#232;les SendAndReceiveReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur de mod&#232;les SendAndReceiveReply
Le modèle **SendAndReceiveReply** permet de créer une paire d'activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> préconfigurées dans une activité <xref:System.Activities.Statements.Sequence> qui sont corrélées dans le cadre d'un modèle d'échange de messages de demande\/réponse sur le client.  
  
## Modèle SendAndReceiveReply  
 L'ajout du modèle **SendAndReceiveReply** effectue trois opérations en plus de créer des activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> dans une activité <xref:System.Activities.Statements.Sequence> :  
  
1.  Il configure les propriétés <xref:System.ServiceModel.Activities.Send.OperationName%2A> et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Send>.  
  
2.  Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.  
  
3.  Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.  
  
### Utilisation du concepteur de modèles SendAndReceiveReply  
 Le concepteur d'activités **SendAndReceiveReply** se trouve dans la catégorie **Messagerie** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **SendAndReceiveReply** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées.Cette action crée une activité <xref:System.ServiceModel.Activities.Send> qui peut être configurée avec le concepteur d'activités **Send** et un objet <xref:System.ServiceModel.Activities.ReceiveReply> corrélé qui peut être configuré avec le concepteur **ReceiveReplyForSend**.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation du concepteur **Send** pour configurer l'activité <xref:System.ServiceModel.Activities.Send>, consultez la rubrique [Envoyez](../workflow-designer/send-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation du concepteur **ReceiveReplyForSend** pour configurer l'activité <xref:System.ServiceModel.Activities.ReceiveReply>, consultez la section suivante.  
  
### Propriétés de ReceiveReply  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.ReceiveReply> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>.La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>.Cette propriété ne doit pas être **null**.Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> sont utilisées ensemble sur le côté client pour modéliser un modèle de messagerie de demande\/réponse.Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée.Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.ReceiveReply>.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Spécifie le contenu du message ou du paramètre à recevoir.Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **Contenu** dans la grille des propriétés ou en cliquant sur le bouton **Définir** en regard de l'étiquette **Contenu** dans l'aire du concepteur d'activités **Receive**.Les deux affichent la boîte de dialogue **Définition de contenu**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette zone, consultez la rubrique [Boîte de dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Spécifie la collection d'objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.Cliquez sur le bouton de sélection en regard de la propriété <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette zone, consultez la rubrique [Boîte de dialogue Ajouter des initialiseurs de corrélation](../workflow-designer/add-correlationinitializers-dialog-box.md) .|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Spécifie l'en\-tête d'action du message.S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> **https:\/\/tempuri.org\/{espace de noms du contrat de service}\/{nom du contrat de service}\/{nom de l'opération}.**|  
  
## Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyez](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)