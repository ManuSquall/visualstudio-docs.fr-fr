---
title: "Boîte de dialogue Définition de contenu | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa0276e284f84eb6514fc407c9ce9be9cf24d8c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="content-definition-dialog-box"></a>Boîte de dialogue Définition du contenu
Le **définition du contenu** boîte de dialogue est utilisée dans [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] pour configurer le **contenu** propriétés de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, et <xref:System.ServiceModel.Activities.ReceiveReply> activités. [!INCLUDE[crabout](../test/includes/crabout_md.md)]les concepteurs d’activités qui utilisent cette zone, consultez la [envoyer](../workflow-designer/send-activity-designer.md), [réception](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) rubriques.  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **initialiser la corrélation** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Message**|Spécifie le contenu du message avec le **les données du Message** zone de texte expression et le type à l’aide de la **type de Message** zone de liste déroulante. Par défaut, le **définition du contenu** utilise le <xref:System.ServiceModel.Activities.ReceiveMessageContent>, lequel attend un <xref:System.ServiceModel.Channels.Message> ou un type dans la définition de service de flux de travail de contrat de message.|  
|**Paramètres**|Cliquez sur le **paramètres** case d’option à utiliser <xref:System.ServiceModel.Activities.ReceiveParametersContent>, lequel attend un contrat de données. Utilisez la grille de données pour définir une collection générique des paires clé/valeur <xref:System.Activities.OutArgument> dont les valeurs sont assignées aux paramètres de variables dans le workflow actuel.|  
  
 Le **définition du contenu** boîte de dialogue est utilisée par le **envoyer**, **réception**, **ReceiveAndSendReply**, et  **SendAndReceiveReply** concepteurs. L'accès à ces derniers est semblable dans chaque cas, et le cas Receive est utilisé ici pour illustrer la procédure.  
  
 Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le **réception** Concepteur d’activités et cliquez sur le bouton de sélection en regard du texte (contenu) pour le **contenu** propriété dans la grille des propriétés pour le **définition du contenu**boîte de dialogue.  
  
 Le contenu peut être spécifié dans le **Message** section pour un <xref:System.ServiceModel.Activities.ReceiveMessageContent> activité ou à l’intérieur du **paramètre** section pour un <xref:System.ServiceModel.Activities.ReceiveParametersContent> activité.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide sur l’interface utilisateur du Concepteur de flux de travail](../workflow-designer/workflow-designer-ui-help.md)