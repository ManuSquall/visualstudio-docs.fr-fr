---
title: Concepteur d’activités Concepteur de flux de travail-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650224"
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation

Le concepteur d’activités **InitializeCorrelation** permet de créer et de configurer une activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. L’activité <xref:System.ServiceModel.Activities.InitializeCorrelation> établit une corrélation entre les messages avant leur envoi ou leur réception.

## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation

Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation

Accédez au concepteur d’activités **InitializeCorrelation** dans la catégorie **messagerie** de la **boîte à outils**.

Le concepteur d’activités **InitializeCorrelation** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail. La suppression du concepteur d’activités crée une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de InitializeCorrelation. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **InitializeCorrelation** ou dans la zone **DisplayName** de la fenêtre **Propriétés** .

La <xref:System.ServiceModel.Activities.CorrelationHandle> peut être précisée dans le champ **corrélation** de la fenêtre **Propriétés** de l’aire du concepteur d’activités **InitializeCorrelation** .

Pour afficher la boîte de dialogue **initialiser la corrélation** dans laquelle vous pouvez spécifier le descripteur de corrélation et les paires clé-valeur utilisées pour l’initialiser, sélectionnez le bouton de sélection en regard du champ **CorrelationData** dans la fenêtre **Propriétés** . Ou sélectionnez l’option « Afficher... » texte d’indication sur l’aire du concepteur d’activités **InitializeCorrelation** . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez l’article de la [boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.InitializeCorrelation> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l’utilisation d’une valeur non définie par défaut pour le <xref:System.Activities.Activity.DisplayName%2A> convivial ne soit pas strictement obligatoire, il est recommandé.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez la boîte de dialogue **initialiser la corrélation** pour configurer l' <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez l’article de la [boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)