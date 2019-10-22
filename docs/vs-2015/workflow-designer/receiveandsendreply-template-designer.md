---
title: Concepteur de modèles ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e853967f73c99aa52958754e9f59f644c2f9497b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672539"
---
# <a name="receiveandsendreply-template-designer"></a>Concepteur de modèles ReceiveAndSendReply
Le modèle **ReceiveAndSendReply** est utilisé pour créer une paire d’activités préconfigurées <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> au sein d’une activité <xref:System.Activities.Statements.Sequence> qui sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le serveur.

## <a name="the-receiveandsendreply-template"></a>Modèle ReceiveAndSendReply
 L’ajout du modèle **ReceiveAndSendReply** effectue trois opérations en plus de la création du <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> activités avec une activité <xref:System.Activities.Statements.Sequence> :

1. Il configure les propriétés <xref:System.ServiceModel.Activities.Receive.OperationName%2A> et <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Receive>.

2. Il lie la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.Receive> à l'activité <xref:System.ServiceModel.Activities.Send>.

3. Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilisation du concepteur de modèles ReceiveAndSendReply
 Le concepteur d’activités **ReceiveAndSendReply** se trouve dans la catégorie **messagerie** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la **vue** , ou CTRL + ALT + X.)

 Le concepteur d’activités **ReceiveAndSendReply** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées. Cela crée une activité <xref:System.ServiceModel.Activities.Receive> qui peut être configurée avec le concepteur d’activités **Send** et un <xref:System.ServiceModel.Activities.SendReply> corrélé qui peut être configuré avec SendReplyToReceive designer.

 [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide du concepteur de **réception** pour configurer l’activité de <xref:System.ServiceModel.Activities.Receive>, consultez la rubrique [Receive](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide du concepteur **SendReplyToReceive** pour configurer l’activité de <xref:System.ServiceModel.Activities.SendReply>, consultez la section suivante.

### <a name="properties-of-sendreply"></a>Propriétés de SendReply
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.SendReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                               Nom de propriété                                | Obligatoire |                                                                                                                                                                                                                                                                                                                                                      Utilisation                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.SendReply>. La valeur par défaut est SendReplyToReceive.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Référence à l'activité <xref:System.ServiceModel.Activities.Receive> associée à cette activité <xref:System.ServiceModel.Activities.SendReply>. Cette propriété ne doit pas être **null**. Les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sont utilisées ensemble sur le serveur pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **contenu** dans la grille des propriétés ou en cliquant sur le bouton **définir...** à côté de l’étiquette **contenu** sur l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . [!INCLUDE[crabout](../includes/crabout-md.md)] comment utiliser cette zone, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de cette zone, consultez la rubrique de la boîte de [dialogue Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Spécifie l'en-tête Action header du message. S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> <strong>espace de noms de contrat de https://tempuri.org/{service }/{nom du nom de contrat} l’opération}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Spécifie si l'instance de workflow doit être persistante avant que le message de réponse ne soit envoyé. La valeur par défaut est **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Voir aussi
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)