---
title: Concepteur de flux de travail - Envoyer concepteur d’activité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395221"
---
# <a name="send-activity-designer"></a>Concepteur d'activités Send

Le concepteur d’activités **Send** est <xref:System.ServiceModel.Activities.Send> utilisé pour créer et configurer une activité.

## <a name="the-send-activity"></a>Activité Send

 Une activité <xref:System.ServiceModel.Activities.Send> permet d'envoyer un message à un service. Une activité <xref:System.ServiceModel.Activities.ReceiveReply> peut être liée à une activité <xref:System.ServiceModel.Activities.Send> qui reçoit un message dans le cadre d'un modèle d'échange de messages de demande/réponse sur le client.

### <a name="using-the-send-activity-designer"></a>Utilisation du concepteur d'activités Send

Accédez au concepteur d’activités **Envoyer** dans la catégorie **Messagerie** de la Boîte **à outils**. Le concepteur d’activités **Send** peut être traîné de la boîte à **outils** et déposé sur la surface Workflow Designer partout où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Send> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Send. Le <xref:System.Activities.Activity.DisplayName%2A> peut être édité dans l’en-tête du concepteur d’activité **Envoyer** ou dans la boîte **DisplayName** de la grille de propriété.

Pour créer <xref:System.ServiceModel.Activities.ReceiveReply> une activité et <xref:System.ServiceModel.Activities.Send> la lier à l’activité sélectionnée, cliquez à droite sur le concepteur d’activités **Envoyer,** cliquez sur l’élément **Create ReceiveReply** dans le menu contextuelle et le concepteur **ReceiveReplyForSend** apparaît ci-dessous le concepteur **Send.** L’activité <xref:System.ServiceModel.Activities.ReceiveReply> est une activité qui reçoit un message dans le cadre d’un modèle d’échange de messages de demande/réponse sur le client. Il peut être configuré avec le concepteur **ReceiveReplyForSend.**

Alternativement, le concepteur de modèle **SendAndReceiveReply** dans la catégorie **Messagerie** de la boîte <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> à **outils** peut être utilisé pour créer une paire d’activités pré-configurées et. Pour plus d’informations sur l’utilisation des modèles **SendAndReceiveReply** et **ReceiveReplyForSend,** consultez le sujet [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Propriétés de l'activité Send

Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.Send> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans le réseau de propriétés ou sur la surface de Workflow Designer.

| Nom de la propriété | Obligatoire | Usage |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nom convivial de l'activité <xref:System.ServiceModel.Activities.Send>. La valeur par défaut est Send. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Nom de l'opération de service appelée par cette activité <xref:System.ServiceModel.Activities.Send>. Cette propriété est utilisée pour construire la valeur par défaut pour la propriété **Action** si la propriété **Action n’est** pas explicitement définie. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Nom du contrat de service que le service à appeler implémente. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en sélectionnant le bouton ellipsis à côté du champ **de contenu** dans la grille de propriété ou en cliquant sur le bouton **Définir...** à côté de **l’étiquette De contenu** sur la surface du concepteur d’activités **Recevoir.** Les deux affichent le dialogue **de définition de** contenu. Pour plus d’informations sur la façon d’utiliser cette boîte, consultez le sujet de la [boîte de dialogue de définition de](../workflow-designer/content-definition-dialog-box.md) contenu. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.<br /><br /> Cliquez sur le bouton ellipsis à côté de la <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> propriété dans la grille de propriétés pour ouvrir la boîte de dialogue Expression **Editor.** Pour plus d’informations sur l’utilisation de cette boîte de dialogue, voir le [thème Comment utiliser l’éditeur d’expression.](../workflow-designer/how-to-use-the-expression-editor.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Spécifie la collection d’objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Send> dans le workflow. Cliquez sur le bouton ellipsis à côté de la <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriété dans la grille de propriétés pour ouvrir la boîte de dialogue Add Correlation **Initializers.** Pour plus d’informations sur l’utilisation de cette boîte, voir le sujet [Add CorrelationInitializers Dialog Box.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Collection de types connus pour l'opération de service que cette activité <xref:System.ServiceModel.Activities.Send> doit appeler. Cette propriété doit être utilisée conjointement à la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> affectée de la valeur <xref:System.Runtime.Serialization.DataContractSerializer>. Elle est ignorée si <xref:System.Xml.Serialization.XmlSerializer> est utilisé.<br /><br /> Sélectionnez le bouton ellipsis à côté du champ **KnownTypes** dans la grille de propriété pour afficher le dialogue **Type Collection Editor** avec lequel vous pouvez ajouter des types pertinents.<br /><br /> Sélectionnez le bouton ellipsis à côté du champ **KnownTypes** dans la grille de propriété pour afficher la boîte de dialogue **Type Collection Editor** avec laquelle vous pouvez ajouter des types pertinents. Pour plus d’informations sur l’utilisation de cette boîte, consultez le sujet [Dialog Box de l’éditeur de collection type.](../workflow-designer/type-collection-editor-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Spécifie l'objet <xref:System.Net.Security.ProtectionLevel> du message.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> signifie l’authentification seulement.<br />2. <xref:System.Net.Security.ProtectionLevel> signifie signer des données pour aider à assurer l’intégrité des données transmises.<br />3. <xref:System.Net.Security.ProtectionLevel> signifie chiffrer et signer des données pour aider à assurer la confidentialité et l’intégrité des données transmises. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Sérialiseur à utiliser pour l'opération de service que l'activité <xref:System.ServiceModel.Activities.Send> doit appeler. La valeur par défaut est <xref:System.Runtime.Serialization.DataContractSerializer>, qui sérialise et désérialise une instance d'un type dans un flux ou document XML utilisant un contrat de données fourni. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Spécifie l'en-tête Action header du message. S’il n’est pas explicitement défini, sa valeur est par défaut à : `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. En cas de spécification sur une activité <xref:System.ServiceModel.Activities.Send>, l'activité <xref:System.ServiceModel.Activities.Receive> qui reçoit le message doit avoir la même valeur pour que le message puisse être remis correctement. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> autorisé pour le récepteur du message. Il définit les niveaux d’usurpation d’identité de sécurité, qui régissent la mesure dans laquelle un processus serveur peut agir au nom d’un processus client.<xref:System.Security.Principal.TokenImpersonationLevel>  indique qu'aucun niveau d'emprunt d'identité n'est assigné. <xref:System.Security.Principal.TokenImpersonationLevel>indique que le processus serveur ne peut pas obtenir d’informations d’identification sur le client et qu’il ne peut pas se faire passer pour le client. <xref:System.Security.Principal.TokenImpersonationLevel>indique que le processus serveur peut obtenir des informations sur le client, tels que les identifiants de sécurité et les privilèges, mais qu’il ne peut pas se faire passer pour le client. Ce niveau est utile pour les serveurs qui exportent leurs propres objets, par exemple, les produits de base de données qui exportent des tables et des vues. À l'aide des informations de sécurité de client récupérées, le serveur peut prendre des décisions concernant la validation d'accès sans pouvoir utiliser d'autres services utilisant le contexte de sécurité du client. <xref:System.Security.Principal.TokenImpersonationLevel>indique que le processus serveur peut usurper l’identité du contexte de sécurité du client sur son système local. Le serveur ne peut pas emprunter l'identité du client sur les systèmes distants. <xref:System.Security.Principal.TokenImpersonationLevel>indique que le processus serveur peut usurper l’identité du contexte de sécurité du client sur les systèmes distants. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> auquel l'activité <xref:System.ServiceModel.Activities.Send> envoie le message. Si cette propriété <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> est définie, la propriété doit être **nulle**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> auquel le message est envoyé. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nom de la configuration du point de terminaison. Cette propriété est définie lorsque vous configurez un point de terminaison dans un fichier de configuration. Cette propriété doit être définie au nom donné dans le ** \<point de terminaison>** élément de votre fichier de configuration. Si cette propriété est <xref:System.ServiceModel.Activities.Send.Endpoint%2A> définie, la propriété doit être **nulle**. |

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Recevoir](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)