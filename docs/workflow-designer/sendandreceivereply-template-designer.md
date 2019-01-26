---
title: Concepteur de flux de travail - Concepteur de modèles SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469e8ca3c325b04684e9481957c2e6bf9e14cffb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940412"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply

Le **SendAndReceiveReply** modèle est utilisé pour créer une paire de préconfiguré <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> activités. Les activités font partie d’un <xref:System.Activities.Statements.Sequence> activité et sont mis en corrélation dans le cadre d’un modèle d’échange de messages demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Modèle SendAndReceiveReply

Ajout de la **SendAndReceiveReply** modèle effectue trois opérations en plus de créer le <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> activités au sein d’un <xref:System.Activities.Statements.Sequence> activité :

- Configure le <xref:System.ServiceModel.Activities.Send.OperationName%2A> et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propriétés de la <xref:System.ServiceModel.Activities.Send> activité.

- Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

- Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="use-the-sendandreceivereply-template-designer"></a>Utiliser le Concepteur de modèles SendAndReceiveReply

Accès le **SendAndReceiveReply** Concepteur d’activités dans le **Messaging** catégorie de la **boîte à outils**. Le **SendAndReceiveReply** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées. Suppression du Concepteur d’activités crée un <xref:System.ServiceModel.Activities.Send> activité qui peut être configurée avec le **envoyer** Concepteur d’activités et une corrélation <xref:System.ServiceModel.Activities.ReceiveReply> qui peut être configuré avec le **ReceiveReplyForSend** concepteur.

Pour plus d’informations sur l’utilisation de la **envoyer** designer pour configurer le <xref:System.ServiceModel.Activities.Send> activité, consultez [envoyer](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply

Le tableau suivant présente le <xref:System.ServiceModel.Activities.ReceiveReply> propriétés et décrit leur utilisation dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l’aire du Concepteur de flux de travail.


| Nom de la propriété | Obligatoire | Utilisation |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l’utilisation d’une valeur par défaut pour le nom convivial <xref:System.Activities.Activity.DisplayName%2A> n’est pas strictement obligatoire, il est préférable d’utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **null**. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> sont utilisées ensemble sur le client pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car il est automatiquement lié à la <xref:System.ServiceModel.Activities.Send> activité à partir de laquelle vous avez créé le <xref:System.ServiceModel.Activities.ReceiveReply> activité. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton de sélection en regard le **contenu** champ dans la grille des propriétés, ou en cliquant sur le **définir** situé en regard le **contenu** étiquette sur le **Réception** aire du Concepteur d’activités. Les deux affichent la **définition du contenu** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez [boîte de dialogue de définition de contenu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la **ajouter des initialiseurs de corrélation** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez [boîte de dialogue Ajouter CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Spécifie l'en-tête Action header du message. Si elle n’est pas explicitement définie, sa valeur par défaut est :<br /><br /> <strong>https://tempuri.org/{service espace de noms de contrat} / {nom de contrat de service} / {nom de l’opération}.</strong> |

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)