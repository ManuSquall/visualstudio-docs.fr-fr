---
title: Concepteur de modèles SendAndReceiveReply
description: Découvrez comment vous pouvez utiliser le modèle SendAndReceiveReply dans Concepteur de flux de travail pour créer une paire d’activités d’envoi et de ReceiveReply préconfigurées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02bcc4a812a541ea792a190dc21dfbeb3119c008
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943690"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply

Le modèle **SendAndReceiveReply** est utilisé pour créer une paire d’activités et préconfigurées <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Les activités font partie d’une <xref:System.Activities.Statements.Sequence> activité et sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Modèle SendAndReceiveReply

L’ajout du modèle **SendAndReceiveReply** effectue trois opérations en plus de la création des <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> activités et dans une <xref:System.Activities.Statements.Sequence> activité :

- Configure les <xref:System.ServiceModel.Activities.Send.OperationName%2A> Propriétés et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de l' <xref:System.ServiceModel.Activities.Send> activité.

- Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utiliser le concepteur de modèles SendAndReceiveReply

Accédez au concepteur d’activités **SendAndReceiveReply** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **SendAndReceiveReply** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. Le déplacement du concepteur d’activités crée une <xref:System.ServiceModel.Activities.Send> activité qui peut être configurée avec le concepteur d’activités **Send** et une activité corrélée <xref:System.ServiceModel.Activities.ReceiveReply> qui peut être configurée avec le concepteur **ReceiveReplyForSend** .

Pour plus d’informations sur l’utilisation du concepteur d' **envoi** pour configurer l' <xref:System.ServiceModel.Activities.Send> activité, consultez [Envoyer](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply

Le tableau suivant présente les <xref:System.ServiceModel.Activities.ReceiveReply> Propriétés et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur l’aire de Concepteur de flux de travail.

| Nom de la propriété | Obligatoire | Usage |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l’utilisation d’une valeur non définie par défaut pour l’option convivial <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **null**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>les activités et sont utilisées ensemble sur le client pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l' <xref:System.ServiceModel.Activities.Send> activité à partir de laquelle vous avez créé l' <xref:System.ServiceModel.Activities.ReceiveReply> activité. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **contenu** dans la grille des propriétés, ou en cliquant sur le bouton **définir** en regard de l’étiquette **contenu** dans l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . Pour plus d’informations sur l’utilisation de cette zone, consultez boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . Pour plus d’informations sur l’utilisation de cette zone, consultez [Ajouter CorrelationInitializers boîte de dialogue](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas défini explicitement, sa valeur par défaut est :<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Çoive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoi](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)