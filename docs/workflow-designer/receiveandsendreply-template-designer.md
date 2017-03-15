---
title: "Concepteur de mod&#232;les ReceiveAndSendReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Concepteur de mod&#232;les ReceiveAndSendReply
Le modèle **ReceiveAndSendReply** permet de créer une paire d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> préconfigurées dans une activité <xref:System.Activities.Statements.Sequence> qui sont corrélées dans le cadre d'un modèle d'échange de messages de demande\/réponse sur le serveur.  
  
## Modèle ReceiveAndSendReply  
 L'ajout du modèle **ReceiveAndSendReply** effectue trois opérations en plus de créer des activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> avec une activité <xref:System.Activities.Statements.Sequence> :  
  
1.  Il configure les propriétés <xref:System.ServiceModel.Activities.Receive.OperationName%2A> et <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Receive>.  
  
2.  Il lie la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.Receive> à l'activité <xref:System.ServiceModel.Activities.Send>.  
  
3.  Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.  
  
### Utilisation du concepteur de modèles ReceiveAndSendReply  
 Le concepteur d'activités **ReceiveAndSendReply** se trouve dans la catégorie **Messagerie** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **ReceiveAndSendReply** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées.Cette action crée une activité <xref:System.ServiceModel.Activities.Receive> qui peut être configurée avec le concepteur d'activités **Send** et un objet <xref:System.ServiceModel.Activities.SendReply> corrélé qui peut être configuré avec le concepteur SendReplyToReceive.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation du concepteur **Receive** pour configurer l'activité <xref:System.ServiceModel.Activities.Receive>, consultez la rubrique [Receive](../workflow-designer/receive-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation du concepteur **SendReplyToReceive** pour configurer l'activité <xref:System.ServiceModel.Activities.SendReply>, consultez la section suivante.  
  
### Propriétés de SendReply  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.SendReply> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.SendReply>.La valeur par défaut est SendReplyToReceive.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Référence à l'activité <xref:System.ServiceModel.Activities.Receive> associée à cette activité <xref:System.ServiceModel.Activities.SendReply>.Cette propriété ne doit pas être **null**.Les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sont utilisées ensemble sur le côté serveur pour modéliser un modèle de messagerie de demande\/réponse.Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée.Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.SendReply>.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Spécifie le contenu du message ou du paramètre à recevoir.Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **Contenu** dans la grille des propriétés ou en cliquant sur le bouton **Définir** en regard de l'étiquette **Contenu** dans l'aire du concepteur d'activités **Receive**.Les deux affichent la boîte de dialogue **Définition de contenu**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette zone, consultez la rubrique [Boîte de dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Spécifie la collection d'objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.Cliquez sur le bouton de sélection en regard de la propriété <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette zone, consultez la rubrique [Boîte de dialogue Ajouter des initialiseurs de corrélation](../workflow-designer/add-correlationinitializers-dialog-box.md) .|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Spécifie l'en\-tête d'action du message.S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> **https:\/\/tempuri.org\/{espace de noms du contrat de service}\/{nom du contrat de service}\/{nom de l'opération}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Spécifie si l'instance de workflow doit être persistante avant que le message de réponse ne soit envoyé.La valeur par défaut est **false**.|  
  
## Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Envoyez](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)