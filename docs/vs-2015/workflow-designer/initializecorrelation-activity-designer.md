---
title: Concepteur d’activités InitializeCorrelation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9dd9d622785fbfebd8560daf9bf459716381ddbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234024"
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation
Le **InitializeCorrelation** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité qui est utilisée pour établir une corrélation entre les messages avant leur envoi ou leur réception.  
  
## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation  
 Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation  
 Le **InitializeCorrelation** Concepteur d’activités peut être trouvé dans le **Messaging** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**  onglet sur le [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **InitializeCorrelation** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface. Cette opération crée un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InitializeCorrelation** Concepteur d’activités ou dans le  **DisplayName** zone de la **propriétés** fenêtre.  
  
 Le <xref:System.ServiceModel.Activities.CorrelationHandle> peut être spécifie dans le **corrélation** champ **propriétés** fenêtre sur le **InitializeCorrelation** aire du Concepteur d’activités.  
  
 En cliquant sur le bouton d’ellipse outre le **CorrelationData** champ **propriétés** fenêtre ou la « vue... » indicateur de texte sur **InitializeCorrelation** aire du Concepteur d’activités affiche le **initialiser la corrélation** boîte de dialogue dans laquelle vous pouvez spécifier le handle de corrélation et les paires clé-valeur utilisées pour l’initialiser. [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Type Collection](../workflow-designer/type-collection-editor-dialog-box.md) rubrique.  
  
### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.InitializeCorrelation> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez le **initialiser la corrélation** boîte de dialogue pour configurer le <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] l’utilisation cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Type Collection](../workflow-designer/type-collection-editor-dialog-box.md) rubrique.|  
  
## <a name="see-also"></a>Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Réception](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyer](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)