---
title: Concepteur de flux de travail - ajouter la boîte de dialogue d’initialiseurs de corrélation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d54724655db7147c06687aa88a4fe623bb277a45
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756938"
---
# <a name="add-correlationinitializers-dialog-box"></a>Boîte de dialogue Ajouter des initialiseurs de corrélation

Le **ajouter des initialiseurs de corrélation** boîte de dialogue est utilisée dans le Concepteur de flux de travail pour configurer le **CorrelationInitializers** propriétés de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, et <xref:System.ServiceModel.Activities.ReceiveReply> activités. Pour plus d’informations sur les concepteurs d’activités qui utilisent cette zone, consultez la [envoyer](../workflow-designer/send-activity-designer.md), [réception](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), et [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) rubriques.

Les initialiseurs de corrélation dans la collection spécifiée avec cette boîte de dialogue peuvent initialiser les corrélations suivantes entre les activités de messagerie :

- fondé sur une requête
- contexte
- contexte de rappel
- demande-réponse

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **ajouter des initialiseurs de corrélation** boîte de dialogue :

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Ajouter un initialiseur**|Cliquez sur le **ajouter initialize** case pour ajouter un initialiseur supplémentaire à la collection.|
|**Type de corrélation**|Spécifie le type d'initialiseur de corrélation. Quatre types sont disponibles :<br /><br /> 1. Initialiseur de corrélation de rappel pour spécifier un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Initialiseur de corrélation de contexte pour spécifier un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Initialiseur de corrélation demande-réponse pour spécifier un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Initialiseur de corrélation de requête pour spécifier un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Pour modifier le **type de corrélation**<br /><br /> 1. Onglet à la ligne spécifique dans le **ajouter un initialiseur** DataGrid.<br />2. Pour définir le focus **CorrelationTypeComboBox**, appuyez sur **Ctrl**+**onglet**.<br />3. Appuyez sur Alt + flèche bas pour afficher le **ComboBox** et le modifier.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation de messages entrants et sortants. Cette liste est valide uniquement lors de l'utilisation de types <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Pour lancer la boîte de dialogue Ajouter des initialiseurs de corrélation

 Le **ajouter des initialiseurs de corrélation** boîte de dialogue est utilisée par le **envoyer**, **réception**, **ReceiveAndSendReply**, et  **SendAndReceiveReply** concepteurs. L’accès à celles-ci est similaire dans chaque cas et le cas qui implique la **réception** concepteur est utilisé ici pour illustrer la procédure.

 Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont placées. Suppression de la **réception** Concepteur d’activités crée un <xref:System.ServiceModel.Activities.Receive> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de réception. Sélectionnez le **réception** Concepteur d’activités et cliquez sur le bouton de sélection en regard du texte (Collection) pour le **CorrelationInitializers** propriété dans la grille des propriétés pour le **ajouter Initialiseurs de corrélation** la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Ajouter la boîte de dialogue de corrélation](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)