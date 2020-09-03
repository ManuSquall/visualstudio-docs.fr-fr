---
title: Boîte de dialogue Ajouter un CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672036"
---
# <a name="add-correlationinitializers-dialog-box"></a>Boîte de dialogue Ajouter des initialiseurs de corrélation
La boîte de dialogue **Ajouter des initialiseurs de corrélation** est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour configurer les propriétés **CorrelationInitializers** des <xref:System.ServiceModel.Activities.Send> activités, <xref:System.ServiceModel.Activities.Receive> , <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] les concepteurs d’activités qui utilisent cette zone, consultez les rubriques [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Les initialiseurs de corrélation dans la collection spécifiée avec cette boîte de dialogue peuvent initialiser des corrélations basées sur une requête, de contexte, de contexte de rappel ou de demande-réponse entre les activités de messagerie.

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **Ajouter des initialiseurs de corrélation** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Ajouter un initialiseur**|Cliquez sur la zone **Ajouter** un initialiseur pour ajouter un initialiseur supplémentaire à la collection.|
|**Type de corrélation**|Spécifie le type d'initialiseur de corrélation. Quatre types sont disponibles :<br /><br /> 1. initialiseur de corrélation de rappel permettant de spécifier un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. un initialiseur de corrélation de contexte pour spécifier un <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. un initialiseur de corrélation demande-réponse pour spécifier un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. initialiseur de corrélation de requête pour spécifier un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Pour modifier le **typecorrélation**<br /><br /> 1. onglet à la ligne spécifique dans la grille de l' **initialiseur Add** .<br />2. Appuyez sur CTRL + TAB pour définir le focus sur **la valeur correlationtypecombobox**<br />3. Appuyez sur Alt + Pg. suiv pour afficher la **zone de liste** déroulante et la modifier.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation de messages entrants et sortants. Cette liste est valide uniquement lors de l'utilisation de types <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Pour lancer la boîte de dialogue Ajouter des initialiseurs de corrélation
 La boîte de dialogue **Ajouter des initialiseurs de corrélation** est utilisée par les concepteurs **Send**, **Receive**, **ReceiveAndSendReply**et **SendAndReceiveReply** . L’accès à ces derniers est semblable dans chaque cas et le cas qui implique le concepteur de **réception** est utilisé ici pour illustrer la procédure.

 Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception, [!INCLUDE[wfd2](../includes/wfd2-md.md)] là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le concepteur d’activités **Receive** , puis cliquez sur le bouton de sélection en regard du texte (collection) pour la propriété **CorrelationInitializers** dans la grille des propriétés pour afficher la boîte de dialogue **Ajouter des initialiseurs de corrélation** .

## <a name="see-also"></a>Voir aussi
 [Boîte de dialogue Initialiser la corrélation](../workflow-designer/initialize-correlation-dialog-box.md)