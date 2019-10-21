---
title: Concepteur d’activités InitializeCorrelation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659020"
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation
Le concepteur d’activités **InitializeCorrelation** permet de créer et de configurer une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> qui est utilisée pour établir une corrélation entre les messages avant de les envoyer ou de les recevoir.

## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation
 Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation
 Le concepteur d’activités **InitializeCorrelation** se trouve dans la catégorie **messagerie** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la vue).menu ou CTRL + ALT + X.)

 Le concepteur d’activités **InitializeCorrelation** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Cela crée une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de InitializeCorrelation. vous pouvez modifier le <xref:System.Activities.Activity.DisplayName%2A> dans l’en-tête du concepteur d’activités **InitializeCorrelation** ou dans la zone **DisplayName** de la fenêtre **Propriétés** .

 La <xref:System.ServiceModel.Activities.CorrelationHandle> peut être précisée dans le champ **corrélation** de la fenêtre **Propriétés** de l’aire du concepteur d’activités **InitializeCorrelation** .

 En cliquant sur le bouton de sélection en regard du champ **CorrelationData** dans la fenêtre **Propriétés** ou de l’option « Afficher... » texte d’indication sur l’aire du concepteur d’activités **InitializeCorrelation** affiche la boîte de dialogue **initialiser la corrélation** dans laquelle vous pouvez spécifier le descripteur de corrélation et les paires clé-valeur utilisées pour l’initialiser. [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de cette boîte de dialogue, consultez la rubrique de la boîte de [dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.InitializeCorrelation> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou sur [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez la boîte de dialogue **initialiser la corrélation** pour configurer l' <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] la boîte de dialogue utiliser cette boîte de dialogue, consultez la rubrique de la boîte de [dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Voir aussi
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)