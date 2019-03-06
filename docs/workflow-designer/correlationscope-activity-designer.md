---
title: Concepteur de flux de travail - Concepteur d’activités CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ca5955cae8d9b2cb1012e97f034d497bbc79e9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953176"
---
# <a name="correlationscope-activity-designer"></a>Concepteur d'activités CorrelationScope

Le **CorrelationScope** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.CorrelationScope> activité qui fournit une gestion implicite des activités de messagerie enfants à l’aide un <xref:System.ServiceModel.Activities.CorrelationHandle> objet.

## <a name="the-correlationscope-activity"></a>L’activité CorrelationScope

La propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> contenues dans l'objet <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sont configurées pour utiliser la propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de l'activité <xref:System.ServiceModel.Activities.CorrelationScope> conteneur pour effectuer la corrélation.

### <a name="use-the-correlationscope-activity-designer"></a>Utiliser le Concepteur d’activités CorrelationScope

Le **CorrelationScope** Concepteur d’activités peut être trouvé dans le **Messaging** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet sur le côté gauche du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le **CorrelationScope** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail. Cette opération crée un <xref:System.ServiceModel.Activities.CorrelationScope> activité avec une valeur par défaut **DisplayName** de CorrelationScope. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **CorrelationScope** Concepteur d’activités ou dans le **DisplayName** boîte de le **propriétés** fenêtre.

Pour spécifier le <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé par les activités de messagerie enfants, sélectionnez le bouton de sélection en regard de la **CorrelatesWith** champ **propriétés** fenêtre pour afficher le **Expression Éditeur** boîte de dialogue. Cette propriété peut également être définie dans l'aire du concepteur d'activités.

Les activités dans la portée de la corrélation sont spécifiées en déposant leurs concepteurs dans les **corps** zone dans le **CorrelationScope** concepteur.

### <a name="the-correlationscope-properties"></a>Les propriétés de CorrelationScope

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.CorrelationScope> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur l’aire du Concepteur de flux de travail et souvent dans les deux.

|Nom de la propriété|Obligatoire|Utilisation|
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