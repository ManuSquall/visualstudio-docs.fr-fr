---
title: Concepteur de flux de travail - Concepteur de modèles de receiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395299"
---
# <a name="receiveandsendreply-template-designer"></a>Concepteur de modèles ReceiveAndSendReply

Le modèle **ReceiveAndSendReply** est utilisé pour créer <xref:System.ServiceModel.Activities.Receive> une <xref:System.ServiceModel.Activities.SendReply> paire d’activités préconfigurées et. Les activités font <xref:System.Activities.Statements.Sequence> partie d’une activité et sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le serveur.

## <a name="the-receiveandsendreply-template"></a>Le modèle ReceiveAndSendReply

L’ajout **d’un modèle ReceiveAndSendReply** fait trois choses en plus de créer le et <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> les activités avec une <xref:System.Activities.Statements.Sequence> activité:

- Configure les <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> propriétés <xref:System.ServiceModel.Activities.Receive> et les propriétés de l’activité.

- Il lie la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.Receive> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-receiveandsendreply-template-designer"></a>Utilisez le concepteur de modèles ReceiveAndSendReply

Accédez au concepteur d’activités **ReceiveAndSendReply** dans la catégorie **Messagerie** de la **Boîte à outils**. Le concepteur **d’activités ReceiveAndSendReply** peut être traîné de la boîte à **outils** et déposé sur la surface Workflow Designer partout où les activités sont généralement placées. L’abandon du <xref:System.ServiceModel.Activities.Receive> concepteur d’activité crée une activité qui peut <xref:System.ServiceModel.Activities.SendReply> être configurée avec le concepteur d’activité **Envoyer** et une corrélation qui peut être configurée avec le concepteur SendReplyToReceive.

Pour plus d’informations sur l’utilisation du concepteur **Receive** pour configurer l’activité, <xref:System.ServiceModel.Activities.Receive> voir [Recevoir Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propriétés de SendReply

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.SendReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines peuvent être modifiées sur la surface Workflow Designer.

| Nom de la propriété | Obligatoire | Usage |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.SendReply>. La valeur par défaut est SendReplyToReceive.<br /><br /> Bien que l’utilisation d’une <xref:System.Activities.Activity.DisplayName%2A> valeur non-default pour le sympathique n’est pas strictement nécessaire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Receive> associée à cette activité <xref:System.ServiceModel.Activities.SendReply>. Cette propriété ne doit pas être **nulle**. <xref:System.ServiceModel.Activities.Receive>et <xref:System.ServiceModel.Activities.SendReply> les activités sont utilisées ensemble sur le serveur pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette <xref:System.ServiceModel.Activities.Send> propriété car elle <xref:System.ServiceModel.Activities.SendReply> est automatiquement liée à l’activité à partir de laquelle vous avez créé l’activité. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton ellipsis à côté du champ **de contenu** dans la grille de propriété, ou en cliquant sur le bouton **Définir** à côté **de l’étiquette de contenu** sur la surface du concepteur d’activités **Recevoir.** Les deux affichent le dialogue **de définition de** contenu. Pour plus d’informations sur la façon d’utiliser cette boîte, consultez le sujet de la [boîte de dialogue de définition de](../workflow-designer/content-definition-dialog-box.md) contenu. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton ellipsis à côté de la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propriété dans la grille de propriétés pour ouvrir la boîte de dialogue Add Correlation **Initializers.** Pour plus d’informations sur l’utilisation de cette boîte, voir le sujet [Add CorrelationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas explicitement défini, sa valeur est par défaut pour :<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Spécifie si l'instance de workflow doit être persistante avant que le message de réponse ne soit envoyé. La valeur par défaut est **false**. |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recevoir](../workflow-designer/receive-activity-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)