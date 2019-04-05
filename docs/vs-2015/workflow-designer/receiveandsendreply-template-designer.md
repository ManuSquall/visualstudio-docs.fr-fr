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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 39c8a88a3c0e798734a55aac66136e15d86d7e17
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947135"
---
# <a name="receiveandsendreply-template-designer"></a>Concepteur de modèles ReceiveAndSendReply
Le **ReceiveAndSendReply** modèle est utilisé pour créer une paire de préconfiguré <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> activités au sein d’un <xref:System.Activities.Statements.Sequence> activité qui sont corrélées dans le cadre d’un échange de messages de demande/réponse modèle sur le serveur.  

## <a name="the-receiveandsendreply-template"></a>Modèle ReceiveAndSendReply  
 Ajout de **ReceiveAndSendReply** modèle effectue trois opérations en plus de créer le <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> activités avec un <xref:System.Activities.Statements.Sequence> activité :  

1.  Il configure les propriétés <xref:System.ServiceModel.Activities.Receive.OperationName%2A> et <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de l'activité <xref:System.ServiceModel.Activities.Receive>.  

2.  Il lie la propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> de l'activité <xref:System.ServiceModel.Activities.Receive> à l'activité <xref:System.ServiceModel.Activities.Send>.  

3.  Il crée un objet <xref:System.ServiceModel.Activities.CorrelationHandle> comme variable dans l'activité parente.  

### <a name="using-the-receiveandsendreply-template-designer"></a>Utilisation du concepteur de modèles ReceiveAndSendReply  
 Le **ReceiveAndSendReply** Concepteur d’activités peut être trouvé dans le **Messaging** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**  onglet [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  

 Le **ReceiveAndSendReply** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées. Cette opération crée un <xref:System.ServiceModel.Activities.Receive> activité qui peut être configurée avec le **envoyer** Concepteur d’activités et une corrélation <xref:System.ServiceModel.Activities.SendReply> qui peut être configuré avec le concepteur SendReplyToReceive.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de la **réception** designer pour configurer le <xref:System.ServiceModel.Activities.Receive> activité, consultez le [réception](../workflow-designer/receive-activity-designer.md) rubrique.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] à l’aide de la **SendReplyToReceive** designer pour configurer le <xref:System.ServiceModel.Activities.SendReply> activité, consultez la section suivante.  

### <a name="properties-of-sendreply"></a>Propriétés de SendReply  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.SendReply> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].  


|                               Nom de la propriété                                | Obligatoire |                                                                                                                                                                                                                                                                                                                                                      Utilisation                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.SendReply>. La valeur par défaut est SendReplyToReceive.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Référence à l'activité <xref:System.ServiceModel.Activities.Receive> associée à cette activité <xref:System.ServiceModel.Activities.SendReply>. Cette propriété ne doit pas être **null**. Les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sont utilisées ensemble sur le serveur pour modéliser un modèle de messagerie de demande/réponse. Cette propriété spécifie l'activité <xref:System.ServiceModel.Activities.Send> qui est associée. Dans le concepteur, vous ne pouvez pas modifier cette propriété, car elle est automatiquement liée à l'activité <xref:System.ServiceModel.Activities.Send> à partir de laquelle vous avez créé l'activité <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton de sélection en regard de la **contenu** champ dans la grille des propriétés ou en cliquant sur le **définir...** bouton en regard de la **contenu** de l’étiquette sur le **réception** aire du Concepteur d’activités. Les deux affichent la **définition du contenu** boîte de dialogue. [!INCLUDE[crabout](../includes/crabout-md.md)] comment utiliser cette zone, consultez la [boîte de dialogue de définition de contenu](../workflow-designer/content-definition-dialog-box.md) rubrique.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la **ajouter des initialiseurs de corrélation** boîte de dialogue. [!INCLUDE[crabout](../includes/crabout-md.md)] l’utilisation de cette zone, consultez la [boîte de dialogue Ajouter CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) rubrique.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Spécifie l'en-tête Action header du message. S'il n'est pas défini explicitement, sa valeur par défaut est :<br /><br /> <strong>https://tempuri.org/{service espace de noms de contrat} / {nom de contrat de service} / {nom de l’opération}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Spécifie si l'instance de workflow doit être persistante avant que le message de réponse ne soit envoyé. La valeur par défaut est **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Voir aussi  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Réception](../workflow-designer/receive-activity-designer.md)   
 [Envoyer](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)