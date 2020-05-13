---
title: SendAndReceiveReply Template Designer (fr) Microsoft Docs
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
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395343"
---
# <a name="sendandreceivereply-template-designer"></a>Concepteur de modèles SendAndReceiveReply
Le modèle **SendAndReceiveReply** est utilisé pour créer <xref:System.ServiceModel.Activities.Send> une <xref:System.ServiceModel.Activities.ReceiveReply> paire <xref:System.Activities.Statements.Sequence> d’activités préconfigurées et au sein d’une activité qui est corrélée dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client.

## <a name="the-sendandreceivereply-template"></a>Modèle SendAndReceiveReply
 L’ajout du modèle **SendAndReceiveReply** <xref:System.ServiceModel.Activities.ReceiveReply> fait trois <xref:System.Activities.Statements.Sequence> choses en plus de créer le et les activités au sein d’une <xref:System.ServiceModel.Activities.Send> activité:

1. Il configure les propriétés <xref:System.ServiceModel.Activities.Send.OperationName%2A> et <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Send>.

2. Il lie la propriété <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.ReceiveReply> à l'activité <xref:System.ServiceModel.Activities.Send>.

3. Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.

### <a name="using-the-sendandreceivereply-template-designer"></a>Utilisation du concepteur de modèles SendAndReceiveReply
 Le concepteur **d’activités SendAndReceiveReply** se trouve dans la catégorie **Messagerie** de la Boîte [!INCLUDE[wfd2](../includes/wfd2-md.md)] à **outils**, qui est accessible en cliquant sur l’onglet **Toolbox** (Alternativement, sélectionnez **toolbar** du menu **View,** ou CTRL-ALT-X.)

 Le concepteur **d’activité SendAndReceiveReply** peut être traîné de [!INCLUDE[wfd2](../includes/wfd2-md.md)] la boîte à **outils** et laissé tomber à la surface partout où les activités sont généralement placées. Cela crée <xref:System.ServiceModel.Activities.Send> une activité qui peut être configurée avec <xref:System.ServiceModel.Activities.ReceiveReply> le concepteur d’activité **Envoyer** et une corrélation qui peut être configurée avec le concepteur **ReceiveReplyForSend.**

 [!INCLUDE[crabout](../includes/crabout-md.md)]en **Send** utilisant le concepteur <xref:System.ServiceModel.Activities.Send> Envoyer pour configurer l’activité, voir le sujet [Envoyer.](../workflow-designer/send-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]en utilisant le concepteur **ReceiveReplyForSend** pour configurer l’activité, <xref:System.ServiceModel.Activities.ReceiveReply> voir la section suivante.

### <a name="properties-of-receivereply"></a>Propriétés de ReceiveReply
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.ReceiveReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|                                 Nom de la propriété                                 | Obligatoire |                                                                                                                                                                                                                                                                                                                                                        Usage                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. La valeur par défaut est ReceiveReplyForSend.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Référence à l'activité <xref:System.ServiceModel.Activities.Send> associée à cette activité <xref:System.ServiceModel.Activities.ReceiveReply>. Cette propriété ne doit pas être **nulle**. <xref:System.ServiceModel.Activities.Send>et <xref:System.ServiceModel.Activities.ReceiveReply> les activités sont utilisées ensemble sur le client pour modéliser un modèle de demande/messagerie de réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton ellipse à côté du champ **de contenu** dans la grille de propriété ou en cliquant sur le **Définir ...** bouton à côté de **l’étiquette de contenu** sur la surface du concepteur d’activités **Recevoir.** Les deux affichent le dialogue **de définition de** contenu. [!INCLUDE[crabout](../includes/crabout-md.md)]comment utiliser cette boîte, voir le sujet De la [catégorie de dialogue de définition de](../workflow-designer/content-definition-dialog-box.md) contenu.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton ellipsis à côté de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille de propriétés pour ouvrir la boîte de dialogue Add Correlation **Initializers.** [!INCLUDE[crabout](../includes/crabout-md.md)]en utilisant cette boîte, voir le [sujet Add CorrelationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Spécifie l'en-tête Action header du message. S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Voir aussi
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Recevez](../workflow-designer/receive-activity-designer.md) [ReçuAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Envoyer](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)