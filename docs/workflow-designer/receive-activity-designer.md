---
title: Concepteur d’activités Concepteur de flux de travail-Receive
description: En savoir plus sur l’activité Receive et sur l’utilisation du concepteur d’activités Receive pour créer et configurer une activité Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceff7d40ffd0d7c961f07dd65a8070a8f11a1b4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899381"
---
# <a name="receive-activity-designer"></a>Concepteur d'activités Receive

Le concepteur d’activités **Receive** est utilisé pour créer et configurer une <xref:System.ServiceModel.Activities.Receive> activité. Une activité <xref:System.ServiceModel.Activities.Receive> est une activité qui reçoit un message qui peut être un type intégré, tel que <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> ou <xref:System.Xml.Linq.XElement>, ou un contrat de données défini par l'application, un contrat de message ou une classe XML sérialisable.

## <a name="the-receive-activity"></a>Activité Receive

L'activité <xref:System.ServiceModel.Activities.Receive> peut recevoir un élément unique ou plusieurs éléments selon le type de contenu de réception utilisé. Une activité <xref:System.ServiceModel.Activities.SendReply> peut être liée à une activité <xref:System.ServiceModel.Activities.Receive> qui reçoit un message dans le cadre d’un modèle d’échange de messages de demande/réponse sur le service.

### <a name="using-the-receive-activity-designer"></a>Utilisation du concepteur d'activités Receive

Accédez au concepteur d’activités **Receive** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Receive** ou dans la zone **DisplayName** de la grille des propriétés.

Pour créer une <xref:System.ServiceModel.Activities.SendReply> activité et la lier à l' <xref:System.ServiceModel.Activities.Receive> activité sélectionnée, cliquez avec le bouton droit sur le concepteur d’activités **Receive** , cliquez sur l’élément **créer un SendReply** dans le menu contextuel et le concepteur **SendReplyToReceive** apparaît sous le concepteur de **réception** . L’activité <xref:System.ServiceModel.Activities.SendReply> est une activité qui envoie le message de réponse dans le cadre d’un modèle d’échange de messages de demande/réponse sur le service. Il peut être configuré avec **SendReplyToReceive** designer.

Le concepteur de modèles **ReceiveAndSendReply** dans la catégorie **messagerie** de la **boîte à outils** peut également être utilisé pour créer une paire d’activités et préconfigurées <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Pour plus d’informations sur l’utilisation du modèle **ReceiveAndSendReply** et **SendReplyToReceive** , consultez la rubrique [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Propriétés de l'activité Receive

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.Receive> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire de Concepteur de flux de travail. Seule la propriété <xref:System.ServiceModel.Activities.Receive.OperationName%2A> est obligatoire.

| Nom de la propriété | Obligatoire | Utilisation |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Spécifie le nom convivial de l'activité <xref:System.ServiceModel.Activities.Receive>. La valeur par défaut est Receive.<br /><br /> Bien que l'utilisation d'une valeur autre que celle par défaut pour le nom convivial de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'utiliser une telle valeur. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Spécifie le nom de l'opération de service implémenté par cette activité <xref:System.ServiceModel.Activities.Receive>. Cette propriété est utilisée pour construire la valeur par défaut de la propriété d' **action** si la propriété d' **action** n’est pas définie explicitement. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Spécifie le nom du contrat de service. Cette propriété permet de regrouper des opérations de service dans des contrats de service individuels. Toutes les activités <xref:System.ServiceModel.Activities.Receive> qui ont le même <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> sont regroupées dans le même contrat de service (type de port WSDL). La valeur par défaut est le nom CLR complet de l’activité de niveau supérieur (racine). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en sélectionnant le bouton de sélection en regard du champ **contenu** dans la grille des propriétés ou en cliquant sur le bouton **définir** en regard de l’étiquette **contenu** sur l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Spécifie les corrélations entre des activités <xref:System.ServiceModel.Activities.Receive> dans des opérations de service d'un workflow avec un objet <xref:System.ServiceModel.MessageQuerySet>. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Définition CorrelatesOn** . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.<br /><br /> Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **éditeur d’expressions** . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la rubrique [Comment : utiliser l’éditeur d’expressions](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Spécifie une valeur qui détermine si une nouvelle instance de workflow est créée pour traiter le message si le message n'est pas corrélé à une instance de workflow existante. Si la valeur est définie sur **true**, une nouvelle instance de workflow est créée pour traiter le message lorsque le message n’est pas corrélé avec une instance de flux de travail existante. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Spécifie une collection de types connus pour l'opération de service implémentée par cette activité <xref:System.ServiceModel.Activities.Receive>. Cette propriété doit être utilisée conjointement à la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> affectée de la valeur <xref:System.Runtime.Serialization.DataContractSerializer>. Elle est ignorée si <xref:System.Xml.Serialization.XmlSerializer> est utilisé.<br /><br /> Sélectionnez le bouton de sélection en regard du champ **KnownTypes** dans la grille des propriétés pour afficher la boîte de dialogue **éditeur de collections** de types qui vous permet d’ajouter des types pertinents. Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Spécifie l'objet <xref:System.Net.Security.ProtectionLevel> du message.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> signifie authentification uniquement.<br />2.  <xref:System.Net.Security.ProtectionLevel> signifie que les données sont signées pour aider à garantir l’intégrité des données transmises.<br />3.  <xref:System.Net.Security.ProtectionLevel> signifie chiffrer et signer des données pour garantir la confidentialité et l’intégrité des données transmises. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Spécifie le type de sérialiseur à utiliser pour l'opération de service implémentée par l'activité <xref:System.ServiceModel.Activities.Receive>. La valeur par défaut est <xref:System.Runtime.Serialization.DataContractSerializer>, qui sérialise et désérialise une instance d'un type dans un flux ou document XML utilisant un contrat de données fourni. <xref:System.Xml.Serialization.XmlSerializer> peut également être utilisé s'il est nécessaire de mieux contrôler les données XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas défini explicitement, sa valeur par défaut est : `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoi](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
