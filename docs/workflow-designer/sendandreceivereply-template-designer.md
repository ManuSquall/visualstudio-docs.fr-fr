---
title: Concepteur de flux de travail-concepteur de modèles SendAndReceiveReply
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
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649956"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply

Le modèle **SendAndReceiveReply** est utilisé pour créer une paire d’activités préconfigurées <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply>. Les activités font partie d’une activité de <xref:System.Activities.Statements.Sequence> et sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Modèle SendAndReceiveReply

L’ajout du modèle **SendAndReceiveReply** effectue trois opérations en plus de la création de l' <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> activités dans une activité <xref:System.Activities.Statements.Sequence> :

- Configure les propriétés <xref:System.ServiceModel.Activities.Send.OperationName%2A> et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de l’activité <xref:System.ServiceModel.Activities.Send>.

- Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utiliser le concepteur de modèles SendAndReceiveReply

Accédez au concepteur d’activités **SendAndReceiveReply** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **SendAndReceiveReply** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. La suppression du concepteur d’activités crée une activité <xref:System.ServiceModel.Activities.Send> qui peut être configurée avec le concepteur d’activités **Send** et un <xref:System.ServiceModel.Activities.ReceiveReply> corrélé qui peut être configuré avec **ReceiveReplyForSend** designer.

Pour plus d’informations sur l’utilisation du concepteur d' **envoi** pour configurer l’activité <xref:System.ServiceModel.Activities.Send>, consultez [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.ReceiveReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur l’aire de Concepteur de flux de travail.

| Nom de propriété | Obligatoire | Utilisation |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l’utilisation d’une valeur non définie par défaut pour le <xref:System.Activities.Activity.DisplayName%2A> convivial ne soit pas strictement obligatoire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **null**. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> sont utilisées ensemble sur le client pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l’activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l’activité <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **contenu** dans la grille des propriétés, ou en cliquant sur le bouton **définir** en regard de l’étiquette **contenu** dans l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . Pour plus d’informations sur l’utilisation de cette zone, consultez boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . Pour plus d’informations sur l’utilisation de cette zone, consultez [Ajouter CorrelationInitializers boîte de dialogue](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas défini explicitement, sa valeur par défaut est :<br /><br /> <strong>espace de noms de contrat de https://tempuri.org/{service }/{nom du nom de contrat} l’opération}.</strong> |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)