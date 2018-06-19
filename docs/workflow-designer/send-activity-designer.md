---
title: Concepteur de flux de travail - Concepteur d’activités Send
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 099a512bcbca7136541c9896e32f43b9e518ed8b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978347"
---
# <a name="send-activity-designer"></a>Concepteur d'activités Send

Le **envoyer** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.Send> activité.

## <a name="the-send-activity"></a>Activité Send

 Une activité <xref:System.ServiceModel.Activities.Send> permet d'envoyer un message à un service. Une activité <xref:System.ServiceModel.Activities.ReceiveReply> peut être liée à une activité <xref:System.ServiceModel.Activities.Send> qui reçoit un message dans le cadre d'un modèle d'échange de messages de demande/réponse sur le client.

### <a name="using-the-send-activity-designer"></a>Utilisation du concepteur d'activités Send
 Le **envoyer** Concepteur d’activités peut être trouvé dans le **messagerie** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet dans le Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **envoyer** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Send> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Send. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **envoyer** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

 Pour créer un <xref:System.ServiceModel.Activities.ReceiveReply> activité et le lier au <xref:System.ServiceModel.Activities.Send> activité, avec le bouton droit le **envoyer** cliquez sur Générateur d’activité le **Create ReceiveReply** élément dans le menu contextuel et le **ReceiveReplyForSend** concepteur apparaît sous le **envoyer** concepteur. L'activité <xref:System.ServiceModel.Activities.ReceiveReply> est une activité qui reçoit un message dans le cadre d'un modèle d'échange de messages de demande/réponse sur le client. Il peut être configuré avec le **ReceiveReplyForSend** concepteur.

 Vous pouvez également le **SendAndReceiveReply** Concepteur de modèles dans le **messagerie** catégorie de la **boîte à outils** peut être utilisé pour créer une paire de préconfiguré<xref:System.ServiceModel.Activities.Send>et <xref:System.ServiceModel.Activities.ReceiveReply> activités. Pour plus d’informations sur l’utilisation de la **SendAndReceiveReply** et **ReceiveReplyForSend** modèles, consultez la [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) rubrique.

### <a name="the-send-activity-properties"></a>Propriétés de l'activité Send
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.Send> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.ServiceModel.Activities.Send>. La valeur par défaut est Send. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|Nom de l'opération de service appelée par cette activité <xref:System.ServiceModel.Activities.Send>. Cette propriété est utilisée pour construire la valeur par défaut pour le **Action** propriété si le **Action** propriété n’est pas définie explicitement.|
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|True|Nom du contrat de service que le service à appeler implémente.|
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|Spécifie le contenu du message ou du paramètre à recevoir. Il peut s'agir d'une activité <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou d'une activité <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Modifier cette propriété en cliquant sur le bouton de sélection en regard de la **contenu** champ dans la grille des propriétés ou en cliquant sur le **définir...**  en regard du **contenu** l’étiquette sur le **réception** aire du Concepteur d’activité. Les deux affichent la **définition du contenu** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue de définition de contenu](../workflow-designer/content-definition-dialog-box.md) rubrique.|
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.<br /><br /> Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> propriété dans la grille des propriétés pour ouvrir la **l’éditeur d’Expression** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez la [Comment : utiliser l’éditeur d’Expression](../workflow-designer/how-to-use-the-expression-editor.md) rubrique.|
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|Spécifie la collection d'objets <xref:System.ServiceModel.Activities.CorrelationInitializer> initialisant plusieurs objets <xref:System.ServiceModel.Activities.CorrelationHandle> qui configurent cette activité <xref:System.ServiceModel.Activities.Send> dans le workflow. Cliquez sur le bouton de sélection en regard du <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriété dans la grille des propriétés pour ouvrir la **ajouter des initialiseurs de corrélation** boîte de dialogue. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue Ajouter CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) rubrique.|
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|Collection de types connus pour l'opération de service que cette activité <xref:System.ServiceModel.Activities.Send> doit appeler. Cette propriété doit être utilisée conjointement à la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> affectée de la valeur <xref:System.Runtime.Serialization.DataContractSerializer>. Elle est ignorée si <xref:System.Xml.Serialization.XmlSerializer> est utilisé.<br /><br /> Cliquez sur le bouton de sélection en regard de la **KnownTypes** champ dans la grille des propriétés pour afficher la **éditeur de collections Type** boîte de dialogue avec laquelle vous pouvez ajouter des types pertinents.<br /><br /> Cliquez sur le bouton de sélection en regard de la **KnownTypes** champ dans la grille des propriétés pour afficher la **éditeur de collections Type** boîte de dialogue avec laquelle vous pouvez ajouter des types pertinents. Pour plus d’informations sur l’utilisation de cette zone, consultez la [boîte de dialogue Éditeur de Collection de Type](../workflow-designer/type-collection-editor-dialog-box.md) rubrique.|
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|True|Spécifie l'objet <xref:System.Net.Security.ProtectionLevel> du message.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> signifie que l’authentification uniquement.<br />2. <xref:System.Net.Security.ProtectionLevel> signifie la signature des données pour garantir l’intégrité des données transmises.<br />3. <xref:System.Net.Security.ProtectionLevel> signifie chiffrer et signer des données pour garantir la confidentialité et l’intégrité des données transmises.|
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|True|Sérialiseur à utiliser pour l'opération de service que l'activité <xref:System.ServiceModel.Activities.Send> doit appeler. La valeur par défaut est <xref:System.Runtime.Serialization.DataContractSerializer>, qui sérialise et désérialise une instance d'un type dans un flux ou document XML utilisant un contrat de données fourni.|
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|Spécifie l'en-tête Action header du message. Si elle n’est pas définie explicitement, sa valeur par défaut : https://tempuri.org/{service espace de noms de contrat} / {nom de contrat de service} / {nom de l’opération}. En cas de spécification sur une activité <xref:System.ServiceModel.Activities.Send>, l'activité <xref:System.ServiceModel.Activities.Receive> qui reçoit le message doit avoir la même valeur pour que le message puisse être remis correctement.|
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel> autorisé pour le récepteur du message. Il définit des niveaux d’emprunt d’identité de sécurité qui régissent le degré auquel un processus serveur peut agir pour le compte d’un processus client.<xref:System.Security.Principal.TokenImpersonationLevel> Indique qu’un niveau d’emprunt d’identité n’est pas affecté. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur ne peut pas obtenir d'informations d'identification à propos du client et ne peut pas emprunter l'identité du client. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut obtenir des informations sur le client, telles que les identificateurs de sécurité et les privilèges, mais il ne peut pas emprunter l'identité du client. Ce niveau est utile pour les serveurs qui exportent leurs propres objets, par exemple, les produits de base de données qui exportent des tables et des vues. À l'aide des informations de sécurité de client récupérées, le serveur peut prendre des décisions concernant la validation d'accès sans pouvoir utiliser d'autres services utilisant le contexte de sécurité du client. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut emprunter l'identité du contexte de sécurité du client sur le système local. Le serveur ne peut pas emprunter l'identité du client sur les systèmes distants. <xref:System.Security.Principal.TokenImpersonationLevel> indique que le processus serveur peut emprunter l'identité du contexte de sécurité du client sur les systèmes distants.|
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint> auquel l'activité <xref:System.ServiceModel.Activities.Send> envoie le message. Si cette propriété est définie la <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> la propriété doit être **null**.|
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||<xref:System.ServiceModel.EndpointAddress> auquel le message est envoyé.|
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||Nom de la configuration du point de terminaison. Cette propriété est définie lorsque vous configurez un point de terminaison dans un fichier de configuration. Cette propriété doit être définie pour le nom donné dans le  **\<point de terminaison >** élément dans votre fichier de configuration. Si cette propriété est définie, le <xref:System.ServiceModel.Activities.Send.Endpoint%2A> la propriété doit être **null**.|

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Réception](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)