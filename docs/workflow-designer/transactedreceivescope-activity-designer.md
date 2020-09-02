---
title: Concepteur d’activités Concepteur de flux de travail-TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75fb1da392bce7dbd0cd7849d83b3b452521e0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875928"
---
# <a name="transactedreceivescope-activity-designer"></a>Concepteur d'activités TransactedReceiveScope

**TransactedReceiveScope** Designer est utilisé pour créer et configurer une <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité.

## <a name="the-transactedreceivescope-activity"></a>Activité TransactedReceiveScope

L’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> vous permet de transmettre une transaction dans des transactions de serveur créées par un workflow ou un répartiteur.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilisation du concepteur d'activités TransactedReceiveScope

Accédez au concepteur d’activités **TransactedReceiveScope** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **TransactedReceiveScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. Cette opération crée une <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité avec un **DisplayName** par défaut de TransactedReceiveScope. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **TransactedReceiveScope** ou dans la zone **DisplayName** de la grille des propriétés.

**TransactedReceiveScope** designer contient des zones de **demande** et de **corps** . Celles-ci sont utilisées pour configurer la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, laquelle spécifie une activité <xref:System.ServiceModel.Activities.Receive>, et une propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, laquelle spécifie un autre objet <xref:System.Activities.Activity>. La propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crée une transaction. La transaction est ensuite rendue ambiante pour l'étendue de la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> afin que toute activité dans cette étendue s'exécute à l'intérieur de cette transaction.

### <a name="the-transactedreceivescope-properties"></a>Propriétés de TransactedReceiveScope

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.TransactedReceiveScope> et décrit comment elles sont utilisées dans le concepteur. Ces <xref:System.Activities.Activity.DisplayName%2A> propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire de concepteur de flux de travail, mais les autres doivent être modifiées sur l’aire de conception.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. La valeur par défaut est TransactedReceiveScope.<br /><br /> Bien que le nom de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Vrai|Supprime une <xref:System.ServiceModel.Activities.Receive> activité dans le bloc de **requête** sur l’aire du concepteur d’activités.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Faux|Dépose un <xref:System.Activities.Activity> dans le bloc de **corps** sur l’aire du concepteur d’activités.|

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Çoive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)