---
title: Concepteur de flux de travail - boîte de dialogue Définition du contenu
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc434e35755b04054d1e24da97e8a4699af7df0e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757949"
---
# <a name="content-definition-dialog-box"></a>Boîte de dialogue Définition du contenu

Le **définition du contenu** boîte de dialogue est utilisée dans le Concepteur de flux de travail pour configurer le **contenu** propriétés de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, et <xref:System.ServiceModel.Activities.ReceiveReply> activités. Pour plus d’informations sur les concepteurs d’activités qui utilisent cette zone, consultez la [envoyer](../workflow-designer/send-activity-designer.md), [réception](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), et [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) rubriques.

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **initialiser la corrélation** boîte de dialogue :

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Message**|Spécifie le contenu du message avec le **données du Message** zone de texte expression et le type à l’aide de la **type de Message** zone de liste déroulante. Par défaut, le **définition du contenu** utilise le <xref:System.ServiceModel.Activities.ReceiveMessageContent>, lequel attend un <xref:System.ServiceModel.Channels.Message> ou un type dans la définition de service de workflow de contrat de message.|
|**Paramètres**|Cliquez sur le **paramètres** case d’option à utiliser <xref:System.ServiceModel.Activities.ReceiveParametersContent>, lequel attend un contrat de données. Utilisez la grille de données pour définir une collection générique des paires clé/valeur <xref:System.Activities.OutArgument> dont les valeurs sont assignées aux paramètres de variables dans le workflow actuel.|

Le **définition du contenu** boîte de dialogue est utilisée par le **envoyer**, **réception**, **ReceiveAndSendReply**, et  **SendAndReceiveReply** concepteurs. L'accès à ces derniers est semblable dans chaque cas, et le cas Receive est utilisé ici pour illustrer la procédure.

Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le **réception** Concepteur d’activités et cliquez sur le bouton de sélection en regard du texte (contenu) pour le **contenu** propriété dans la grille des propriétés pour le **définition du contenu**la boîte de dialogue.

Le contenu peut être spécifié dans le **Message** section pour un <xref:System.ServiceModel.Activities.ReceiveMessageContent> activité ou à l’intérieur du **paramètre** section pour un <xref:System.ServiceModel.Activities.ReceiveParametersContent> activité.

## <a name="see-also"></a>Voir aussi

- [Aide sur l’interface utilisateur du Concepteur de flux de travail](../workflow-designer/workflow-designer-ui-help.md)