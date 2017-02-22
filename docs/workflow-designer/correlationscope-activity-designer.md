---
title: "Concepteur d&#39;activit&#233;s CorrelationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s CorrelationScope
Le concepteur d'activités **CorrelationScope** permet de créer et configurer une activité <xref:System.ServiceModel.Activities.CorrelationScope> qui fournit une gestion implicite des activités de messagerie enfants à l'aide d'un objet <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
## Activité CorrelationScope  
 La propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants.Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> contenues dans l'objet <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sont configurées pour utiliser la propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de l'activité <xref:System.ServiceModel.Activities.CorrelationScope> conteneur pour effectuer la corrélation.  
  
### Utilisation du concepteur d'activités CorrelationScope  
 Le concepteur d'activités **CorrelationScope** se trouve dans la catégorie **Messagerie** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **CorrelationScope** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Cette action crée une activité <xref:System.ServiceModel.Activities.CorrelationScope> avec CorrelationScope comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **CorrelationScope** ou dans la zone **DisplayName** de la fenêtre **Propriétés**.  
  
 Pour spécifier l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé par les activités de messagerie enfants, cliquez sur le bouton de sélection situé en regard du champ **CorrelatesWith** dans la fenêtre **Propriétés** pour afficher la boîte de dialogue **Éditeur d'expressions**.Cette propriété peut également être définie dans l'aire du concepteur d'activités.  
  
 Les activités dont l'étendue est limitée par la corrélation sont spécifiées en déposant leurs concepteurs de la zone **Body** dans le concepteur **CorrelationScope**.  
  
### Propriétés de CorrelationScope  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.CorrelationScope> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], et souvent dans les deux.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants.Si vous ne définissez pas cette propriété, <xref:System.ServiceModel.Activities.CorrelationScope> crée automatiquement un objet <xref:System.ServiceModel.Activities.CorrelationHandle> implicite.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Spécifie les activités dans l'étendue de la corrélation.|  
  
## Voir aussi  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyez](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)