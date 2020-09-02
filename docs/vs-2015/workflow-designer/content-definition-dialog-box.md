---
title: Boîte de dialogue Définition du contenu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656956"
---
# <a name="content-definition-dialog-box"></a>Boîte de dialogue Définition du contenu
La boîte de dialogue **définition du contenu** est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour configurer les propriétés de **contenu** des <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> activités,, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] les concepteurs d’activités qui utilisent cette zone, consultez les rubriques [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **initialiser la corrélation** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Message**|Spécifie le contenu du message avec la zone de texte expression de **données du message** et le type à l’aide de la zone de liste déroulante **type de message** . Par défaut, la **définition de contenu** utilise <xref:System.ServiceModel.Activities.ReceiveMessageContent> , qui attend un <xref:System.ServiceModel.Channels.Message> ou un type de contrat de message dans la définition du service de Workflow.|
|**Paramètres**|Cliquez sur la case d’option **paramètres** pour utiliser <xref:System.ServiceModel.Activities.ReceiveParametersContent> , qui attend un contrat de données. Utilisez la grille de données pour définir une collection générique des paires clé/valeur <xref:System.Activities.OutArgument> dont les valeurs sont assignées aux paramètres de variables dans le workflow actuel.|

 La boîte de dialogue **définition du contenu** est utilisée par les concepteurs **Send**, **Receive**, **ReceiveAndSendReply**et **SendAndReceiveReply** . L'accès à ces derniers est semblable dans chaque cas, et le cas Receive est utilisé ici pour illustrer la procédure.

 Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception, [!INCLUDE[wfd2](../includes/wfd2-md.md)] là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le concepteur d’activités **Receive** , puis cliquez sur le bouton de sélection en regard du texte (contenu) de la propriété **contenu** dans la grille des propriétés pour afficher la boîte de dialogue **définition du contenu** .

 Le contenu peut être spécifié dans la section de **message** pour une <xref:System.ServiceModel.Activities.ReceiveMessageContent> activité ou dans la section de **paramètre** d’une <xref:System.ServiceModel.Activities.ReceiveParametersContent> activité.

## <a name="see-also"></a>Voir aussi
 [Aide sur l'interface utilisateur de Workflow Designer](../workflow-designer/workflow-designer-ui-help.md)