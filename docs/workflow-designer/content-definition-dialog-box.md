---
title: "Bo&#238;te de dialogue D&#233;finition du contenu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Bo&#238;te de dialogue D&#233;finition du contenu
La boîte de dialogue **Définition du contenu** est utilisée dans [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] pour configurer les propriétés **Content** des activités <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] les concepteurs d'activités qui utilisent cette zone, consultez les rubriques [Envoyez](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 Le tableau suivant décrit les éléments d'interface utilisateur de la boîte de dialogue **Définition du contenu**.  
  
|Élément d'interface|Description|  
|-------------------------|-----------------|  
|**Message**|Spécifie le contenu du message avec la zone de texte de l'expression **Données de message** et le type à l'aide de la zone de liste déroulante **Type de message**.Par défaut, la **Définition du contenu** utilise l'objet <xref:System.ServiceModel.Activities.ReceiveMessageContent>, lequel attend un objet <xref:System.ServiceModel.Channels.Message> ou un type de contrat de message dans la définition du service de workflow.|  
|**Paramètres**|Cliquez sur la case d'option **Paramètres** pour utiliser l'objet <xref:System.ServiceModel.Activities.ReceiveParametersContent>, lequel attend un contrat de données.Utilisez la grille de données pour définir une collection générique des paires clé\/valeur <xref:System.Activities.OutArgument> dont les valeurs sont assignées aux paramètres de variables dans le workflow actuel.|  
  
 La boîte de dialogue **Définition du contenu** est utilisée par les concepteurs **Send**, **Receive**, **ReceiveAndSendReply** et **SendAndReceiveReply**.L'accès à ces derniers est semblable dans chaque cas, et le cas Receive est utilisé ici pour illustrer la procédure.  
  
 Le concepteur d'activités **Receive** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées.Cette action crée une activité <xref:System.ServiceModel.Activities.Receive> avec Receive comme <xref:System.Activities.Activity.DisplayName%2A> par défaut.Sélectionnez le concepteur d'activités **Receive**, puis cliquez sur le bouton de sélection en regard de texte \(Contenu\) pour la propriété **Content** dans la grille des propriétés pour afficher la boîte de dialogue **Définition du contenu**.  
  
 Le contenu peut être spécifié dans la section **Message** pour une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou dans la section **Paramètre** pour une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>.  
  
## Voir aussi  
 [Aide sur l'interface utilisateur de Workflow Designer](../workflow-designer/workflow-designer-ui-help.md)