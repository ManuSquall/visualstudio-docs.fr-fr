---
title: Concepteur d’activités CorrelationScope | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63d429d0196283795a6d034bc5f1a0c72773ff42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="correlationscope-activity-designer"></a>Concepteur d'activités CorrelationScope
Le **CorrelationScope** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.CorrelationScope> activité qui fournit une gestion implicite des activités de messagerie enfants à l’aide un <xref:System.ServiceModel.Activities.CorrelationHandle> objet.

## <a name="the-correlationscope-activity"></a>Activité CorrelationScope
 La propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> contenues dans l'objet <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sont configurées pour utiliser la propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de l'activité <xref:System.ServiceModel.Activities.CorrelationScope> conteneur pour effectuer la corrélation.

### <a name="using-the-correlationscope-activity-designer"></a>Utilisation du concepteur d'activités CorrelationScope
 Le **CorrelationScope** Concepteur d’activités peut être trouvé dans le **messagerie** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils** onglet sur le côté gauche de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **CorrelationScope** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface. Cette opération crée un <xref:System.ServiceModel.Activities.CorrelationScope> activité avec une valeur par défaut **DisplayName** de CorrelationScope. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **CorrelationScope** Concepteur d’activités ou dans le **DisplayName** boîte de le **propriétés** fenêtre.

 Pour spécifier le <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé par les activités de messagerie enfants, cliquez sur le bouton de sélection en regard de la **CorrelatesWith** champ **propriétés** fenêtre pour afficher les **l’éditeur d’Expression**  boîte de dialogue. Cette propriété peut également être définie dans l'aire du concepteur d'activités.

 Les activités étendue est limitées par la corrélation sont spécifiées en déposant leurs concepteurs de la **corps** zone dans le **CorrelationScope** concepteur.

### <a name="the-correlationscope-properties"></a>Propriétés de CorrelationScope
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.CorrelationScope> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] aire de conception et souvent à la fois dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Si vous ne définissez pas cette propriété, <xref:System.ServiceModel.Activities.CorrelationScope> crée automatiquement un objet <xref:System.ServiceModel.Activities.CorrelationHandle> implicite.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Spécifie les activités dans l'étendue de la corrélation.|

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Réception](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)