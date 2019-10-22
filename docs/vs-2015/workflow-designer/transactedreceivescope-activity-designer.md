---
title: Concepteur d’activités TransactedReceiveScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4230e4b598553f5fefbc3b97663fd42320ee1e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607018"
---
# <a name="transactedreceivescope-activity-designer"></a>Concepteur d'activités TransactedReceiveScope
**TransactedReceiveScope** Designer est utilisé pour créer et configurer une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

## <a name="the-transactedreceivescope-activity"></a>Activité TransactedReceiveScope
 L’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> vous permet de transmettre une transaction dans des transactions de serveur créées par un workflow ou un répartiteur.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilisation du concepteur d'activités TransactedReceiveScope
 Le concepteur d’activités **TransactedReceiveScope** se trouve dans la catégorie **messagerie** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la **vue** , ou CTRL + ALT + X.)

 Le concepteur d’activités **TransactedReceiveScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées. Cela crée une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> avec un **DisplayName** par défaut de TransactedReceiveScope. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **TransactedReceiveScope** ou dans la zone **DisplayName** de la grille des propriétés.

 **TransactedReceiveScope** designer contient des zones de **demande** et de **corps** . Celles-ci sont utilisées pour configurer la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, laquelle spécifie une activité <xref:System.ServiceModel.Activities.Receive>, et une propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, laquelle spécifie un autre objet <xref:System.Activities.Activity>. La propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crée une transaction. La transaction est ensuite rendue ambiante pour l'étendue de la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> afin que toute activité dans cette étendue s'exécute à l'intérieur de cette transaction.

### <a name="the-transactedreceivescope-properties"></a>Propriétés de TransactedReceiveScope
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.TransactedReceiveScope> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)], mais les autres doivent être modifiés dans l'aire de conception.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. La valeur par défaut est TransactedReceiveScope.<br /><br /> Bien que le nom de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Supprime une activité de <xref:System.ServiceModel.Activities.Receive> dans le bloc de **requête** sur l’aire du concepteur d’activités.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Supprime une <xref:System.Activities.Activity> dans le bloc de **corps** sur l’aire du concepteur d’activités.|

## <a name="see-also"></a>Voir aussi
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)