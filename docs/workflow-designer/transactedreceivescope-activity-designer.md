---
title: "Concepteur d&#39;activit&#233;s TransactedReceiveScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s TransactedReceiveScope
Le concepteur **TransactedReceiveScope** permet de créer et configurer une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
## Activité TransactedReceiveScope  
 L'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> vous permet de transmettre une transaction dans des transactions de serveur créées par un workflow ou un répartiteur.  
  
### Utilisation du concepteur d'activités TransactedReceiveScope  
 Le concepteur d'activités **TransactedReceiveScope** se trouve dans la catégorie **Messagerie** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **TransactedReceiveScope** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées.Cette action crée une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> avec TransactedReceiveScope comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **TransactedReceiveScope** ou dans la zone **DisplayName** de la grille des propriétés.  
  
 Le concepteur **TransactedReceiveScope** contient les zones **Request** et **Body**.Celles\-ci sont utilisées pour configurer la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, laquelle spécifie une activité <xref:System.ServiceModel.Activities.Receive>, et une propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, laquelle spécifie un autre objet <xref:System.Activities.Activity>.La propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crée une transaction.La transaction est ensuite rendue ambiante pour l'étendue de la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> afin que toute activité dans cette étendue s'exécute à l'intérieur de cette transaction.  
  
### Propriétés de TransactedReceiveScope  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.TransactedReceiveScope> et décrit comment elles sont utilisées dans le concepteur.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], mais les autres doivent être modifiés dans l'aire de conception.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>.La valeur par défaut est TransactedReceiveScope.<br /><br /> Bien que le nom de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Dépose une activité <xref:System.ServiceModel.Activities.Receive> dans le bloc **Request** sur la surface du concepteur d'activités.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Dépose une activité <xref:System.Activities.Activity> dans le bloc **Body** sur la surface du concepteur d'activités.|  
  
## Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyez](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)