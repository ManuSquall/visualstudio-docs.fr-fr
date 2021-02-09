---
title: Concepteur d’activités Concepteur de flux de travail-Send
description: En savoir plus sur l’activité d’envoi et sur la façon dont vous pouvez utiliser le concepteur d’activités Send pour créer et configurer une activité d’envoi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b18323f42b67ebb3fb1162432a8b2fd296f2908e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876353"
---
# <a name="send-activity-designer"></a>Concepteur d'activités Send

Le concepteur d’activités **Send** est utilisé pour créer et configurer une <xref:System.ServiceModel.Activities.Send> activité.

## <a name="the-send-activity"></a>Activité Send

 Une activité <xref:System.ServiceModel.Activities.Send> permet d'envoyer un message à un service. Une activité <xref:System.ServiceModel.Activities.ReceiveReply> peut être liée à une activité <xref:System.ServiceModel.Activities.Send> qui reçoit un message dans le cadre d'un modèle d'échange de messages de demande/réponse sur le client.

### <a name="using-the-send-activity-designer"></a>Utilisation du concepteur d'activités Send

Accédez au concepteur d’activités **Send** dans la catégorie **messagerie** de la **boîte à outils**. Le concepteur d’activités **Send** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Send> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Send. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Send** ou dans la zone **DisplayName** de la grille des propriétés.

Pour créer une <xref:System.ServiceModel.Activities.ReceiveReply> activité et la lier à l' <xref:System.ServiceModel.Activities.Send> activité sélectionnée, cliquez avec le bouton droit sur le concepteur d’activités **Send** , cliquez sur l’élément **créer un ReceiveReply** dans le menu contextuel et le concepteur **ReceiveReplyForSend** apparaît sous le concepteur d' **envoi** . L’activité <xref:System.ServiceModel.Activities.ReceiveReply> est une activité qui reçoit un message dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client. Il peut être configuré avec **ReceiveReplyForSend** designer.

Le concepteur de modèles **SendAndReceiveReply** dans la catégorie **messagerie** de la **boîte à outils** peut également être utilisé pour créer une paire d’activités et préconfigurées <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Pour plus d’informations sur l’utilisation des modèles **SendAndReceiveReply** et **ReceiveReplyForSend** , consultez la rubrique [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Propriétés de l'activité Send

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.Send> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire de Concepteur de flux de travail.

| Nom de la propriété | Obligatoire | Utilisation |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial de l'activité <xref:System.ServiceModel.Activities.Send>. La valeur par défaut est Send. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Nom de l'opération de service appelée par cette activité <xref:System.ServiceModel.Activities.Send>. Cette propriété est utilisée pour construire la valeur par défaut de la propriété d' **action** si la propriété d' **action** n’est pas définie explicitement. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Nom du contrat de service que le service à appeler implémente. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifiez cette propriété en sélectionnant le bouton de sélection en regard du champ **contenu** dans la grille des propriétés ou en cliquant sur le bouton **définir** en regard de l’étiquette **contenu** sur l’aire du concepteur d’activités **Receive** . Les deux affichent la boîte de dialogue **définition du contenu** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Définition du contenu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.<br /><br /> Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **éditeur d’expressions** . Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la rubrique [Comment : utiliser l’éditeur d’expressions](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Send> dans le workflow. Cliquez sur le bouton de sélection en regard de la <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la boîte de dialogue **Ajouter des initialiseurs de corrélation** . Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Collection de types connus pour l'opération de service que cette activité <xref:System.ServiceModel.Activities.Send> doit appeler. Cette propriété doit être utilisée conjointement à la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> affectée de la valeur <xref:System.Runtime.Serialization.DataContractSerializer>. Elle est ignorée si <xref:System.Xml.Serialization.XmlSerializer> est utilisé.<br /><br /> Sélectionnez le bouton de sélection en regard du champ **KnownTypes** dans la grille des propriétés pour afficher la boîte de dialogue de l' **éditeur de collections** de types qui vous permet d’ajouter des types pertinents.<br /><br /> Sélectionnez le bouton de sélection en regard du champ **KnownTypes** dans la grille des propriétés pour afficher la boîte de dialogue **éditeur de collections** de types qui vous permet d’ajouter des types pertinents. Pour plus d’informations sur l’utilisation de cette zone, consultez la rubrique de la boîte de [dialogue Éditeur de collections de types](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Spécifie l'objet <xref:System.Net.Security.ProtectionLevel> du message.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> signifie authentification uniquement.<br />2.  <xref:System.Net.Security.ProtectionLevel> signifie que les données sont signées pour aider à garantir l’intégrité des données transmises.<br />3.  <xref:System.Net.Security.ProtectionLevel> signifie chiffrer et signer des données pour garantir la confidentialité et l’intégrité des données transmises. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Sérialiseur à utiliser pour l'opération de service que l'activité <xref:System.ServiceModel.Activities.Send> doit appeler. La valeur par défaut est <xref:System.Runtime.Serialization.DataContractSerializer>, qui sérialise et désérialise une instance d'un type dans un flux ou document XML utilisant un contrat de données fourni. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas défini explicitement, sa valeur par défaut est : `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . En cas de spécification sur une activité <xref:System.ServiceModel.Activities.Send>, l'activité <xref:System.ServiceModel.Activities.Receive> qui reçoit le message doit avoir la même valeur pour que le message puisse être remis correctement. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> autorisé pour le récepteur du message. Il définit les niveaux d’emprunt d’identité de sécurité, qui régissent le degré auquel un processus serveur peut agir pour le compte d’un processus client.<xref:System.Security.Principal.TokenImpersonationLevel>  indique qu'aucun niveau d'emprunt d'identité n'est assigné. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur ne peut pas obtenir d’informations d’identification sur le client et qu’il ne peut pas emprunter l’identité du client. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut obtenir des informations sur le client, telles que les identificateurs de sécurité et les privilèges, mais qu’il ne peut pas emprunter l’identité du client. Ce niveau est utile pour les serveurs qui exportent leurs propres objets, par exemple, les produits de base de données qui exportent des tables et des vues. À l'aide des informations de sécurité de client récupérées, le serveur peut prendre des décisions concernant la validation d'accès sans pouvoir utiliser d'autres services utilisant le contexte de sécurité du client. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut emprunter l’identité du contexte de sécurité du client sur son système local. Le serveur ne peut pas emprunter l'identité du client sur les systèmes distants. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut emprunter l’identité du contexte de sécurité du client sur les systèmes distants. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> auquel l'activité <xref:System.ServiceModel.Activities.Send> envoie le message. Si cette propriété est définie <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> , la propriété doit avoir la **valeur null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> auquel le message est envoyé. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nom de la configuration du point de terminaison. Cette propriété est définie lorsque vous configurez un point de terminaison dans un fichier de configuration. Cette propriété doit être définie sur le nom donné dans l' **\<endpoint>** élément de votre fichier de configuration. Si cette propriété est définie, la <xref:System.ServiceModel.Activities.Send.Endpoint%2A> propriété doit avoir la **valeur null**. |

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Çoive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)