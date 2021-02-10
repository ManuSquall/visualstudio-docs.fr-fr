---
title: Concepteur d'activités InitializeCorrelation
description: Dans Concepteur de flux de travail, Découvrez comment vous pouvez utiliser le concepteur d’activités InitializeCorrelation pour créer et configurer une activité InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9591ef604fcf9374e9aa498e74c5a7761459589f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959790"
---
# <a name="initializecorrelation-activity-designer"></a>Concepteur d'activités InitializeCorrelation

Le concepteur d’activités **InitializeCorrelation** permet de créer et de configurer une <xref:System.ServiceModel.Activities.InitializeCorrelation> activité. L' <xref:System.ServiceModel.Activities.InitializeCorrelation> activité établit une corrélation entre les messages avant de les envoyer ou de les recevoir.

## <a name="the-initializecorrelation-activity"></a>Activité InitializeCorrelation

Une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est utilisée pour initialiser des corrélations sans envoyer ou recevoir de message. En général, la corrélation est initialisée lors de l'envoi ou de la réception d'un message. Si la corrélation doit être établie avant l'envoi ou la réception d'un message, utilisez <xref:System.ServiceModel.Activities.InitializeCorrelation> pour initialiser la corrélation.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilisation du concepteur d'activités InitializeCorrelation

Accédez au concepteur d’activités **InitializeCorrelation** dans la catégorie **messagerie** de la **boîte à outils**.

Le concepteur d’activités **InitializeCorrelation** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail. La suppression du concepteur d’activités crée une <xref:System.ServiceModel.Activities.InitializeCorrelation> activité avec la valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **InitializeCorrelation** ou dans la zone **DisplayName** de la fenêtre **Propriétés** .

<xref:System.ServiceModel.Activities.CorrelationHandle>Peut être spécifie dans le champ **corrélation** de la fenêtre **Propriétés** de l’aire du concepteur d’activités **InitializeCorrelation** .

Pour afficher la boîte de dialogue **initialiser la corrélation** dans laquelle vous pouvez spécifier le descripteur de corrélation et les paires clé-valeur utilisées pour l’initialiser, sélectionnez le bouton de sélection en regard du champ **CorrelationData** dans la fenêtre **Propriétés** . Ou sélectionnez l’option « Afficher... » texte d’indication sur l’aire du concepteur d’activités **InitializeCorrelation** . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez l’article de la [boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propriétés d'InitializeCorrelation

Le tableau suivant présente les <xref:System.ServiceModel.Activities.InitializeCorrelation> Propriétés et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou sur Concepteur de flux de travail surface.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. La valeur par défaut est InitializeCorrelation.<br /><br /> Bien que l’utilisation d’une valeur non définie par défaut pour l’friendly <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour associer des activités de workflow dans la corrélation.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dictionnaire des données de corrélation qui lie les messages à l'instance de workflow.<br /><br /> Utilisez la boîte de dialogue **initialiser la corrélation** pour configurer le <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez l’article de la [boîte de dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Çoive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoi](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)