---
title: Concepteur de flux de travail - SendAndReceiveReply Template Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395247"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply

Le modèle **SendAndReceiveReply** est utilisé pour créer <xref:System.ServiceModel.Activities.Send> une <xref:System.ServiceModel.Activities.ReceiveReply> paire d’activités préconfigurées et. Les activités font <xref:System.Activities.Statements.Sequence> partie d’une activité et sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Le modèle SendAndReceiveReply

L’ajout du modèle **SendAndReceiveReply** <xref:System.ServiceModel.Activities.Send> fait <xref:System.ServiceModel.Activities.ReceiveReply> trois <xref:System.Activities.Statements.Sequence> choses en plus de créer le et les activités au sein d’une activité:

- Configure les <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propriétés <xref:System.ServiceModel.Activities.Send> et les propriétés de l’activité.

- Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utilisez le concepteur de modèles SendAndReceiveReply

Accédez au concepteur d’activités **SendAndReceiveReply** dans la catégorie **Messagerie** de la **Boîte à outils.** Le concepteur **d’activités SendAndReceiveReply** peut être traîné de la boîte à **outils** et déposé sur la surface Workflow Designer partout où les activités sont généralement placées. L’abandon du <xref:System.ServiceModel.Activities.Send> concepteur d’activité crée une activité qui peut <xref:System.ServiceModel.Activities.ReceiveReply> être configurée avec le concepteur d’activité **Envoyer** et une corrélation qui peut être configurée avec le concepteur **ReceiveReplyForSend.**

Pour plus d’informations sur l’utilisation du concepteur **Envoyer** pour configurer l’activité, <xref:System.ServiceModel.Activities.Send> voir [Envoyer](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply

Le tableau suivant <xref:System.ServiceModel.Activities.ReceiveReply> montre les propriétés et décrit comment ils sont utilisés dans le concepteur. Ces propriétés peuvent être modifiées dans le réseau de propriétés, et certaines peuvent être modifiées sur la surface de Workflow Designer.

| Nom de la propriété | Obligatoire | Usage |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l’utilisation d’une <xref:System.Activities.Activity.DisplayName%2A> valeur non-default pour le sympathique n’est pas strictement nécessaire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **nulle**. <xref:System.ServiceModel.Activities.Send>et <xref:System.ServiceModel.Activities.ReceiveReply> les activités sont utilisées ensemble sur le client pour modéliser un modèle de demande/messagerie de réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette <xref:System.ServiceModel.Activities.Send> propriété car elle <xref:System.ServiceModel.Activities.ReceiveReply> est automatiquement liée à l’activité à partir de laquelle vous avez créé l’activité. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton ellipsis à côté du champ **de contenu** dans la grille de propriété, ou en cliquant sur le bouton **Définir** à côté **de l’étiquette de contenu** sur la surface du concepteur d’activités **Recevoir.** Les deux affichent le dialogue **de définition de** contenu. Pour plus d’informations sur la façon d’utiliser cette boîte, voir [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton ellipsis à côté de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille de propriétés pour ouvrir la boîte de dialogue Add Correlation **Initializers.** Pour plus d’informations sur l’utilisation de cette boîte, voir [Add CorrelationInitializers Dialog Box](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas explicitement défini, sa valeur est par défaut pour :<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recevoir](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)