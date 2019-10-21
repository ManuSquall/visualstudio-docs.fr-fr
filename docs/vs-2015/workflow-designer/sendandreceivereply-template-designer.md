---
title: Concepteur de modèles SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663267"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply
Le modèle **SendAndReceiveReply** est utilisé pour créer une paire d’activités préconfigurées <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> au sein d’une activité <xref:System.Activities.Statements.Sequence> qui sont corrélées dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Modèle SendAndReceiveReply
 L’ajout du modèle **SendAndReceiveReply** effectue trois opérations en plus de la création des activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> au sein d’une activité <xref:System.Activities.Statements.Sequence> :

1. Il configure les propriétés <xref:System.ServiceModel.Activities.Send.OperationName%2A> et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Send>.

2. Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

3. Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilisation du concepteur de modèles SendAndReceiveReply
 Le concepteur d’activités **SendAndReceiveReply** se trouve dans la catégorie **messagerie** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la **vue** , ou CTRL + ALT + X.)

 Le concepteur d’activités **SendAndReceiveReply** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées. Cela crée une activité <xref:System.ServiceModel.Activities.Send> qui peut être configurée avec le concepteur d’activités **Send** et un <xref:System.ServiceModel.Activities.ReceiveReply> corrélé qui peut être configuré avec **ReceiveReplyForSend** designer.

 [!INCLUDE[crabout](../includes/crabout-md.md)] l’utilisation du concepteur d' **envoi** pour configurer l’activité de <xref:System.ServiceModel.Activities.Send>, consultez la rubrique [Envoyer](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide du concepteur **ReceiveReplyForSend** pour configurer l’activité de <xref:System.ServiceModel.Activities.ReceiveReply>, consultez la section suivante.

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.ReceiveReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nom de propriété                                 | Obligatoire |                                                                                                                                                                                                                                                                                                                                                        Utilisation                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **null**. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> sont utilisées ensemble sur le client pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en cliquant sur le bouton de sélection en regard du champ **contenu** dans la grille des propriétés ou en cliquant sur le bouton **définir...** à côté de l’étiquette **contenu** sur l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . [!INCLUDE[crabout](../includes/crabout-md.md)] comment utiliser cette zone, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de cette zone, consultez la rubrique de la boîte de [dialogue Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Spécifie l'en-tête Action header du message. S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> <strong>espace de noms de contrat de https://tempuri.org/{service }/{nom du nom de contrat} l’opération}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Voir aussi
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)