---
title: Concepteur d’activités Concepteur de flux de travail-CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e481342f7b7e86b3ce073b7d6a15254ae72d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650581"
---
# <a name="correlationscope-activity-designer"></a>Concepteur d'activités CorrelationScope

Le concepteur d’activités **CorrelationScope** permet de créer et de configurer une activité de <xref:System.ServiceModel.Activities.CorrelationScope> qui fournit une gestion implicite des activités de messagerie enfants à l’aide d’un objet <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>Activité CorrelationScope

La propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> contenues dans l'objet <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sont configurées pour utiliser la propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de l'activité <xref:System.ServiceModel.Activities.CorrelationScope> conteneur pour effectuer la corrélation.

### <a name="use-the-correlationscope-activity-designer"></a>Utiliser le concepteur d’activités CorrelationScope

Le concepteur d’activités **CorrelationScope** se trouve dans la catégorie **messagerie** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** +**ALT** +**X**.

Le concepteur d’activités **CorrelationScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail. Cela crée une activité <xref:System.ServiceModel.Activities.CorrelationScope> avec un **DisplayName** par défaut de CorrelationScope. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **CorrelationScope** ou dans la zone **DisplayName** de la fenêtre **Propriétés** .

Pour spécifier le <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé par les activités de messagerie enfants, sélectionnez le bouton de sélection en regard du champ **CorrelatesWith** dans la fenêtre **Propriétés** pour afficher la boîte de dialogue **éditeur d’expressions** . Cette propriété peut également être définie dans l'aire du concepteur d'activités.

Les activités délimitées au sein de la corrélation sont spécifiées en déposant leurs concepteurs dans la zone de **corps** au sein du concepteur **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Propriétés CorrelationScope

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.CorrelationScope> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la fenêtre **Propriétés** ou sur l’aire de concepteur de flux de travail, et souvent dans les deux.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Si vous ne définissez pas cette propriété, <xref:System.ServiceModel.Activities.CorrelationScope> crée automatiquement un objet <xref:System.ServiceModel.Activities.CorrelationHandle> implicite.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Spécifie les activités dans l'étendue de la corrélation.|

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)