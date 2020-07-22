---
title: Concepteur de flux de travail-concepteur de modèles ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66822664766ac64e466882fda27906f56ebb4aad
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876006"
---
# <a name="receiveandsendreply-template-designer"></a>Concepteur de modèles ReceiveAndSendReply

Le modèle **ReceiveAndSendReply** est utilisé pour créer une paire d’activités et préconfigurées <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Les activités font partie d’une <xref:System.Activities.Statements.Sequence> activité et sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le serveur.

## <a name="the-receiveandsendreply-template"></a>Modèle ReceiveAndSendReply

L’ajout d’un modèle **ReceiveAndSendReply** effectue trois opérations en plus de la création des <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> activités et avec une <xref:System.Activities.Statements.Sequence> activité :

- Configure les <xref:System.ServiceModel.Activities.Receive.OperationName%2A> Propriétés et <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de l' <xref:System.ServiceModel.Activities.Receive> activité.

- Il lie la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.Receive> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-receiveandsendreply-template-designer"></a>Utiliser le concepteur de modèles ReceiveAndSendReply

Accédez au concepteur d’activités **ReceiveAndSendReply** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **ReceiveAndSendReply** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. Le déplacement du concepteur d’activités crée une <xref:System.ServiceModel.Activities.Receive> activité qui peut être configurée avec le concepteur d’activités **Send** et une activité corrélée <xref:System.ServiceModel.Activities.SendReply> qui peut être configurée avec le concepteur SendReplyToReceive.

Pour plus d’informations sur l’utilisation du concepteur de **réception** pour configurer l' <xref:System.ServiceModel.Activities.Receive> activité, consultez le [Concepteur d’activités Receive](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propriétés de SendReply

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.SendReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur l’aire de Concepteur de flux de travail.

| Nom de la propriété | Obligatoire | Usage |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.SendReply>. La valeur par défaut est SendReplyToReceive.<br /><br /> Bien que l’utilisation d’une valeur non définie par défaut pour l’option convivial <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Receive> associée à cette activité <xref:System.ServiceModel.Activities.SendReply>. Cette propriété ne doit pas être **null**. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>les activités et sont utilisées ensemble sur le serveur pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l' <xref:System.ServiceModel.Activities.Send> activité à partir de laquelle vous avez créé l' <xref:System.ServiceModel.Activities.SendReply> activité. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **contenu** dans la grille des propriétés, ou en cliquant sur le bouton **définir** en regard de l’étiquette **contenu** dans l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas défini explicitement, sa valeur par défaut est :<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Spécifie si l'instance de workflow doit être persistante avant que le message de réponse ne soit envoyé. La valeur par défaut est **false**. |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recevoir](../workflow-designer/receive-activity-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)