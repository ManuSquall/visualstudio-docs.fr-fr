---
title: Concepteur de flux de travail boîte de dialogue Ajouter un CorrelationInitializers
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d69b53e21d11cba99a9e897871c6f9e0320352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650774"
---
# <a name="add-correlationinitializers-dialog-box"></a>Boîte de dialogue Ajouter des initialiseurs de corrélation

La boîte de dialogue **Ajouter des initialiseurs de corrélation** est utilisée dans Concepteur de flux de travail pour configurer les propriétés **CorrelationInitializers** des activités <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>. Pour plus d’informations sur les concepteurs d’activités qui utilisent cette zone, consultez les rubriques [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Les initialiseurs de corrélation de la collection spécifiée avec cette boîte de dialogue peuvent initialiser les corrélations suivantes entre les activités de messagerie :

- basé sur une requête
- contexte
- contexte de rappel
- demande-réponse

Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **Ajouter des initialiseurs de corrélation** :

|Élément d'interface utilisateur|Description|
|-|-----------------|
|**Ajouter un initialiseur**|Cliquez sur la zone **Ajouter** un initialiseur pour ajouter un initialiseur supplémentaire à la collection.|
|**Type de corrélation**|Spécifie le type d'initialiseur de corrélation. Quatre types sont disponibles :<br /><br /> 1. initialiseur de corrélation de rappel permettant de spécifier un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. un initialiseur de corrélation de contexte pour spécifier un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. un initialiseur de corrélation demande-réponse pour spécifier un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. initialiseur de corrélation de requête permettant de spécifier un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Pour modifier le **typecorrélation**<br /><br /> 1. onglet à la ligne spécifique dans la grille de l' **initialiseur Add** .<br />2. pour définir le focus sur **la valeur correlationtypecombobox**, appuyez sur **CTRL** +**onglet**.<br />3. Appuyez sur Alt + Pg. suiv pour afficher la **zone de liste** déroulante et la modifier.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation de messages entrants et sortants. Cette liste est valide uniquement lors de l'utilisation de types <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Pour lancer la boîte de dialogue Ajouter des initialiseurs de corrélation

 La boîte de dialogue **Ajouter des initialiseurs de corrélation** est utilisée par les concepteurs **Send**, **Receive**, **ReceiveAndSendReply**et **SendAndReceiveReply** . L’accès à ces derniers est semblable dans chaque cas, et le cas qui implique le concepteur de **réception** est utilisé ici pour illustrer la procédure.

 Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont placées. La suppression du concepteur d’activités **Receive** crée une activité <xref:System.ServiceModel.Activities.Receive> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut Receive. Sélectionnez le concepteur d’activités **Receive** , puis cliquez sur le bouton de sélection en regard du texte (collection) pour la propriété **CorrelationInitializers** dans la grille des propriétés pour afficher la boîte de dialogue **Ajouter des initialiseurs de corrélation** .

## <a name="see-also"></a>Voir aussi

- [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)