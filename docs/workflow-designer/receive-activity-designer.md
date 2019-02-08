---
title: Concepteur d’activités de flux de travail concepteur - Receive
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c75b635cbdce7662c9e3a30237edb3e004ab7d0c
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742441"
---
# <a name="receive-activity-designer"></a>Concepteur d'activités Receive

Le **réception** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.Receive> activité. Une activité <xref:System.ServiceModel.Activities.Receive> est une activité qui reçoit un message qui peut être un type intégré, tel que <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> ou <xref:System.Xml.Linq.XElement>, ou un contrat de données défini par l'application, un contrat de message ou une classe XML sérialisable.

## <a name="the-receive-activity"></a>Activité Receive

L'activité <xref:System.ServiceModel.Activities.Receive> peut recevoir un élément unique ou plusieurs éléments selon le type de contenu de réception utilisé. Une activité <xref:System.ServiceModel.Activities.SendReply> peut être liée à une activité <xref:System.ServiceModel.Activities.Receive> qui reçoit un message dans le cadre d'un modèle d'échange de messages de demande/réponse sur le service.

### <a name="using-the-receive-activity-designer"></a>Utilisation du concepteur d'activités Receive

Accès le **réception** Concepteur d’activités dans le **Messaging** catégorie de la **boîte à outils**. Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **réception** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

Pour créer un <xref:System.ServiceModel.Activities.SendReply> activité et liez-le au <xref:System.ServiceModel.Activities.Receive> activité, avec le bouton droit le **réception** cliquez concepteur, activité le **Create SendReply** élément dans le menu contextuel et le **SendReplyToReceive** concepteur apparaît sous le **réception** concepteur. L’activité <xref:System.ServiceModel.Activities.SendReply> est une activité qui envoie le message de réponse dans le cadre d’un modèle d’échange de messages de demande/réponse sur le service. Il peut être configuré avec le **SendReplyToReceive** concepteur.

Vous pouvez également le **ReceiveAndSendReply** Concepteur de modèles dans le **Messaging** catégorie de la **boîte à outils** peut être utilisé pour créer une paire de préconfiguré<xref:System.ServiceModel.Activities.Receive>et <xref:System.ServiceModel.Activities.SendReply> activité. Pour plus d’informations sur l’utilisation de la **ReceiveAndSendReply** et **SendReplyToReceive** modèle, consultez la [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) rubrique.

### <a name="the-receive-activity-properties"></a>Propriétés de l'activité Receive

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.Receive> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille de propriétés ou sur l’aire du Concepteur de flux de travail. Seule la propriété <xref:System.ServiceModel.Activities.Receive.OperationName%2A> est obligatoire.


| Nom de la propriété | Obligatoire | Utilisation |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Spécifie le nom convivial de l'activité <xref:System.ServiceModel.Activities.Receive>. La valeur par défaut est Receive.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Spécifie le nom de l'opération de service implémenté par cette activité <xref:System.ServiceModel.Activities.Receive>. Cette propriété est utilisée pour construire la valeur par défaut pour le **Action** propriété si le **Action** propriété n’est pas définie explicitement. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Spécifie le nom du contrat de service. Cette propriété permet de regrouper des opérations de service dans des contrats de service individuels. Toutes les activités <xref:System.ServiceModel.Activities.Receive> qui ont le même <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> sont regroupées dans le même contrat de service (type de port WSDL). La valeur par défaut est le nom CLR qualifié complet de l’activité de niveau supérieur (racine). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en sélectionnant le bouton de sélection en regard de la **contenu** champ dans la grille des propriétés ou en cliquant sur le **définir...**  bouton en regard de la **contenu** de l’étiquette sur le **réception** aire du Concepteur d’activités. Les deux affichent la **définition du contenu** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue de définition de contenu](../workflow-designer/content-definition-dialog-box.md) rubrique. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Spécifie les corrélations entre des activités <xref:System.ServiceModel.Activities.Receive> dans des opérations de service d'un workflow avec un objet <xref:System.ServiceModel.MessageQuerySet>. Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété dans la grille des propriétés pour ouvrir la **définition CorrelatesOn** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la [boîte de dialogue de définition de contenu](../workflow-designer/content-definition-dialog-box.md) rubrique. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.<br /><br /> Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> propriété dans la grille des propriétés pour ouvrir la **Éditeur d’Expression** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez le [Comment : Utiliser l’éditeur d’expressions](../workflow-designer/how-to-use-the-expression-editor.md) rubrique. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la **ajouter des initialiseurs de corrélation** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue Ajouter CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) rubrique. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Spécifie une valeur qui détermine si une nouvelle instance de workflow est créée pour traiter le message si le message n'est pas corrélé à une instance de workflow existante. Si la valeur est définie sur **true**, une nouvelle instance de flux de travail est créée pour traiter le message lorsque le message n’est pas mis en corrélation avec une instance de flux de travail existante. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Spécifie une collection de types connus pour l'opération de service implémentée par cette activité <xref:System.ServiceModel.Activities.Receive>. Cette propriété doit être utilisée conjointement à la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> affectée de la valeur <xref:System.Runtime.Serialization.DataContractSerializer>. Elle est ignorée si <xref:System.Xml.Serialization.XmlSerializer> est utilisé.<br /><br /> Sélectionnez le bouton de sélection en regard de la **KnownTypes** champ dans la grille des propriétés pour afficher la **éditeur de collections de Type** boîte de dialogue avec laquelle vous pouvez ajouter des types pertinents. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue Éditeur de Type Collection](../workflow-designer/type-collection-editor-dialog-box.md) rubrique. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Spécifie l'objet <xref:System.Net.Security.ProtectionLevel> du message.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> signifie que l’authentification uniquement.<br />2. <xref:System.Net.Security.ProtectionLevel> signifie la signature des données pour garantir l’intégrité des données transmises.<br />3. <xref:System.Net.Security.ProtectionLevel> signifie chiffrer et signer des données pour garantir la confidentialité et l’intégrité des données transmises. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Spécifie le type de sérialiseur à utiliser pour l'opération de service implémentée par l'activité <xref:System.ServiceModel.Activities.Receive>. La valeur par défaut est <xref:System.Runtime.Serialization.DataContractSerializer>, qui sérialise et désérialise une instance d'un type dans un flux ou document XML utilisant un contrat de données fourni. <xref:System.Xml.Serialization.XmlSerializer> peut également être utilisé s'il est nécessaire de mieux contrôler les données XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Spécifie l'en-tête Action header du message. Si elle n’est pas définie explicitement, sa valeur par défaut : `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
