---
title: "Concepteur d’activités InitializeCorrelation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 83abd9f76f68ec4131840fb0ea58e9aeb93f30d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation
Le **InitializeCorrelation** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité qui est utilisée pour établir une corrélation entre les messages avant leur envoi ou leur réception.  
  
## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation  
 Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation  
 Le **InitializeCorrelation** Concepteur d’activités peut être trouvé dans le **messagerie** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**  onglet sur le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **InitializeCorrelation** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface. Cette opération crée un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InitializeCorrelation** Concepteur d’activités ou dans le  **DisplayName** zone de la **propriétés** fenêtre.  
  
 Le <xref:System.ServiceModel.Activities.CorrelationHandle> peut être spécifie dans le **corrélation** champ **propriétés** fenêtre sur la **InitializeCorrelation** aire du Concepteur d’activité.  
  
 En cliquant sur le bouton de sélection en dehors du **CorrelationData** champ **propriétés** fenêtre ou le texte d’indication « Afficher... » sur **InitializeCorrelation** Concepteur d’activités surface affiche le **initialiser la corrélation** boîte de dialogue dans laquelle vous pouvez spécifier le Gestionnaire de corrélation et les paires clé-valeur utilisées pour l’initialisation. [!INCLUDE[crabout](../test/includes/crabout_md.md)]à l’aide de cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Collection de Type](../workflow-designer/type-collection-editor-dialog-box.md) rubrique.  
  
### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.InitializeCorrelation> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez le **initialiser la corrélation** boîte de dialogue pour configurer le <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../test/includes/crabout_md.md)]l’utilisation cette boîte de dialogue, consultez la [boîte de dialogue Éditeur de Collection de Type](../workflow-designer/type-collection-editor-dialog-box.md) rubrique.|  
  
## <a name="see-also"></a>Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Réception](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyer](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)